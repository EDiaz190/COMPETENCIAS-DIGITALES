const mysql = require('mysql');

// Crear conexión a MySQL
const connection = mysql.createConnection({
  host: 'localhost',
  user: 'root',
  password: 'tu_contraseña',
  database: 'supermercado'
});

connection.connect(err => {
  if (err) throw err;
  console.log('Conectado a la base de datos');
});

// Registrar una venta (Ejemplo: Juan compra 3 unidades de arroz y 2 de leche)
const clienteId = 1; // Juan Perez
const productosVendidos = [{id: 1, cantidad: 3}, {id: 2, cantidad: 2}];

let total = 0;

// Obtener el total de la venta
productosVendidos.forEach(producto => {
  connection.query("SELECT precio FROM productos WHERE id = ?", [producto.id], (err, result) => {
    if (err) throw err;
    total += result[0].precio * producto.cantidad;

    // Una vez que tenemos el total, insertamos la venta
    if (productosVendidos.indexOf(producto) === productosVendidos.length - 1) {
      connection.query("INSERT INTO ventas (cliente_id, total) VALUES (?, ?)", [clienteId, total], (err, result) => {
        if (err) throw err;
        console.log('Venta registrada exitosamente');
        
        // Descontamos el stock de los productos vendidos
        productosVendidos.forEach(producto => {
          connection.query("UPDATE productos SET stock = stock - ? WHERE id = ?", [producto.cantidad, producto.id], (err, result) => {
            if (err) throw err;
          });
        });
      });
    }
  });
});

// Consultar todas las ventas
connection.query("SELECT v.id, c.nombre, v.total, v.fecha FROM ventas v JOIN clientes c ON v.cliente_id = c.id", (err, result) => {
  if (err) throw err;
  console.log(result);
});

connection.end();
