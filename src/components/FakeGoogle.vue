<template>
  <div class="body">
    <nav id="header">
      <ul>
        <li>
          <a href>Gmail</a>
        </li>
        <li>
          <a href>Images</a>
        </li>
        <li>
          <a href>Apps</a>
        </li>
        <li>
          <a href>Iniciar sesión</a>
        </li>
      </ul>
    </nav>

    <div id="container">
      <h1 id="logo">Google</h1>

      <form>
        <input type="text" value="  Cómo ser más productivo en el trabajo">
        <input type="submit" v-on:click="goSearch" value="Buscar con Google">
        <input type="submit" value="Me siento con suerte">
      </form>

      <p>
        <small>
          Ofrecido por Google en:
          <a href> Español (Latinoamérica)</a>
        </small>
      </p>
    </div>
    <!--END OF CONTAINER-->
    <footer>
      <nav class="clearfix">
        <ul class="left-links">
          <li>
            <a href>Publicidad</a>
          </li>
          <li>
            <a href>Negocios</a>
          </li>
          <li>
            <a href>Acerca de</a>
          </li>
        </ul>

        <ul class="right-links">
          <li>
            <a href>Privacidad</a>
          </li>
          <li>
            <a href>Condiciones</a>
          </li>
          <li>
            <a href>Preferencias</a>
          </li>
        </ul>
      </nav>
    </footer>
  </div>
</template>

<style scoped>
.body {
  background-color: #fff;
  height: 100%;
  font-family: Arial, sans-serif;
  font-size: 13px;
}
#container {
  width: 580px;
  margin: 0 auto;
  text-align: center;
}
h1#logo {
  width: 284px;
  height: 95px;
  background: url("https://upload.wikimedia.org/wikipedia/commons/c/c7/GoogleLogoSept12015.png")
    top left no-repeat;
  background-size: 100%;
  text-indent: -99999px;
  margin: 0 auto;
}
form{
  margin-bottom: 20px;
}
input[type="text"] {
  background: #fff;
  width: 580px;
  padding: 10px;
  color: rgba(0,0,0,.87);
  margin: 25px 0 10px;
  border: 1px solid #dfe1e5;
  border-radius: 24px;
  font-size: 16px;
}
input[type="text"]:hover {
  border-color: #aaa;
}
input[type="submit"] {
  height: 36px;
  line-height: 27px;
  background-image: -moz-linear-gradient(top,#f5f5f5,#f1f1f1);
  background-color: #f2f2f2;
  color: #5F6368;
  min-width: 54px;
  padding: 0 16px;
  border-radius: 4px;
  margin: 25px 8px 10px 0;
  border: 1px solid #f2f2f2;
  font-size: 14px;
  font-family: Arial, sans-serif;
  text-align: center;
  border: solid 0.5px #ddd;
}
input[type="submit"]:hover {
  border-color: #ccc;
  border: solid 1px #ccc;
  cursor: pointer;
}
small {
  margin: 0 auto;
  font-size: 12px;
}
a:link,
a:visited {
  color: dodgerblue;
}
nav#header {
  text-align: right;
  padding: 20px;
}
nav#header ul li {
  display: inline;
}

nav#header ul li a:link,
nav#header ul li a:visited,
footer nav ul li a:link,
footer nav ul li a:visited {
  color: rgba(0,0,0,.54);
  line-height: 40px;
  text-decoration: none;
  padding: 11px;
}
nav#header ul li a:hover,
footer nav ul li a:hover {
  text-decoration: underline;
}
footer {
  position: fixed;
  width: 100%;
  bottom: 0;
  background: #f2f2f2;
}
footer nav {
  padding: 0px;
  border-top: 1px solid #e4e4e4;
}
nav ul li {
  display: inline;
}

footer nav ul.right-links {
  float: right;
}
footer nav ul.left-links {
  float: left;
}
.clearfix:after {
  content: "";
  display: table;
  clear: both;
}
</style>

<script>
export default {
  methods: {
    goSearch(e) {
      location.replace("https://www.google.com/search?q=Cómo+ser+más+productivo+en+el+trabajo&btnK=Buscar+con+Google&oq=Cómo+ser+más+productivo+en+el+trabajo");
      e.preventDefault();
    }
  }
}
</script>



