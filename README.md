# Todo-List-with-JavaScript
here is a half part of a todo list, put the checkboxes and give the css are some tasks I have to complete


const todos = JSON.parse(localStorage.getItem("todos")) || [];

const actualizaTodos = (todos) => {
    const todoStrings = JSON.stringify(todos)
    localStorage.setItem("todos", todoStrings)
}

window.onload = () => {
    const form = document.getElementById("todo-form");
        form.onsubmit = (e) => {  
            e.preventDefault();
            const todo = document.getElementById("todo");
            const todoText = todo.value;
            todo.value = "";
            todos.push(todoText)
            console.log(todoText);
            const render = () => {
            const todolist = document.getElementById("todo-list");
            const todosTemplate = todos.map(t => "<li>" + t + "</li>" );
            todolist.innerHTML = todosTemplate.join("");
            const elementos = document.querySelectorAll("#todo-list li");
            elementos.forEach((elemento, i) => {
            elemento.addEventListener("click", () =>{
            elemento.parentNode.removeChild(elemento)
            todos.splice(i, 1)
               
                })
            })
        }
}
