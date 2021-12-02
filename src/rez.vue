else if (this.filter === "active"){ return this.todos.filter(function(todo){
return !todo.completed }) } //completed else (filter === "completed"){ return
this.todos.filter(function(todo){ return todo.completed }) }
