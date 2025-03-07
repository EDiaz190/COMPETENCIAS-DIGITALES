  LISTA DE TAREAS
{URGENTE
    font-family: Arial, sans-serif;
    background-color: #f4f4f4;
    margin: 0;
    padding: 0;
    display: flex;
    justify-content: center;
    align-items: center;
    height: 100vh;
}

.{
    background-color: white;
    padding: 20px;
    border-radius: 10px;
    box-shadow: 0px 4px 6px rgba(0, 0, 0, 0.1);
    text-align: center;
    width: 300px;
}

input[type="text"] {
    padding: 10px;
    width: 80%;
    margin: 10px 0;
    border-radius: 5px;
    border: 1px solid #ccc;
}

button {
    padding: 10px;
    background-color: #4CAF50;
    color: white;
    border: none;
    border-radius: 5px;
    cursor: pointer;
}

button:hover {
    background-color: #45a049;
}

ul {
    list-style-type: none;
    padding: 0;
}

li {
    background-color: #f9f9f9;
    padding: 10px;
    margin: 5px 0;
    border-radius: 5px;
    display: flex;
    justify-content: space-between;
    align-items: center;
}

li.completed {
    text-decoration: line-through;
    background-color: #d3ffd3;
}

button.delete {
    background-color: #f44336;
}

button.delete:hover {
    background-color: #e53935;
}
