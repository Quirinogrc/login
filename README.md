from flask import Flask, render_template_string, request
app = Flask(__name__)

html = """
<form method="post">
  Usuario: <input name="user"><br>
  Clave: <input type="password" name="pwd"><br>
  <input type="submit" value="Login">
</form>
"""

@app.route("/", methods=["GET","POST"])
def login():
    if request.method=="POST":
        if request.form["user"]=="admin" and request.form["pwd"]=="123":
            return "Bienvenido Admin"
        else:
            return "Credenciales incorrectas"
    return render_template_string(html)

if __name__=="__main__":
    app.run(debug=True)
