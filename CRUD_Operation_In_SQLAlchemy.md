# Create a Route (C)
```
bash
@app.route('/',methods=['GET','POST'])
def index():
    
    if(request.method == 'POST'):
        title = request.form.get('title')
        desc = request.form.get('desc')
    
        todo = Todo(title=title,desc=desc)
        db.session.add(todo)
        db.session.commit()
        
    allTodo = Todo.query.all()

    
    return render_template('index.html',allTodo=allTodo)
  

```

# Read an data (R)
```
bash
# Todo : To read a entire todo data
@app.route('/show')
def showData():
    allTodo = Todo.query.all()
    print(allTodo)
    return render_template('index.html',allTodo=allTodo, update=False)

```

# Update the data (U)
```
bash
# Todo : To update a particular todo element
@app.route('/update/<string:sno>', methods=['GET','POST'])
def update(sno):
    todo = Todo.query.filter_by(sno=sno).first()

    if request.method == 'POST':
        todo.title = request.form['title']
        todo.desc = request.form['desc']
        db.session.commit()
        return redirect('/')
    return render_template('index.html',todo=todo, update=True)

```


# Delete an Todo (D)

```
bash
# Todo : To delete a particular todo element
@app.route('/delete/<string:sno>')
def delete(sno):
    todo = Todo.query.filter_by(sno=sno).first()
    db.session.delete(todo)
    db.session.commit()
    return redirect('/')

```
