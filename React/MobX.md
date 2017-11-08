State is the heart of each application.

我们在项目中为什么需要state这个概念，它解决了什么问题？

我们来看MobX官网上的一个例子：

        class TodoStore {
        	todos = [];
        
        	get completedTodosCount() {
            	return this.todos.filter(
        			todo => todo.completed === true
        		).length;
            }
        
        	report() {
        		if (this.todos.length === 0)
        			return "<none>";
        		return `Next todo: "${this.todos[0].task}". ` +
        			`Progress: ${this.completedTodosCount}/${this.todos.length}`;
        	}
        
            addTodo(task) {
        		this.todos.push({
        			task: task,
        			completed: false,
                    assignee: null
        		});
        	}
        }
        
        const todoStore = new TodoStore();
        
这个TodoStore类的功能十分简单，就是维护一个todo列表，那么它和所谓的state有什么关系呢？

So far, there is nothing special about this code.

But what if we did not have to call report explicitly, but could just declare that we want it to be invoked upon each state change?

That would free us from the responsibility of calling report from any place in our code base that might affect the report.

That is exactly what MobX can do for you.

哇，这就是我们在项目中实践状态管理的意义。

To achieve that, 