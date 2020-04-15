<template>
<div id="app">
  <div class="header">
    <router-link to="/">
      <div class="logo">
        <img src="/logo.png">
      </div>
    </router-link>
    <div class="title">
      <h1>Jared Rossberg's Photography Portfolio</h1>
    </div>
  </div>
  <div class="content">
    <router-view />
  </div>
  <div class="footer">
    <router-link to="/admin">Admin</router-link>
    <p>View source code on <a
        href="https://github.com/BYU-CS-260-Winter-2020/lab-4-museum-of-ordinary-objects-jaredrossberg">Github</a></p>
  </div>
</div>
</template>

<style>
html {
  box-sizing: border-box;
}

body {
  font-family: 'Montserrat', sans-serif;
  font-size: 16px;
  background: #fff;
  padding: 0px;
  margin: 0px;
}

/* Header */
.header {
  display: flex;
  padding: 10px 100px 0px 100px;
  background-color: rgb(7, 88, 22);
  color: rgba(255, 255, 255, 0.705);
}

.logo {
    width: 150px;
    height: 120px;
}

.logo img {
    width: 100%;
    height: auto;
}

.title {
  margin-top: 5px;
}

.title h1 {
  font-size: 30px;
}

.content {
  padding: 20px 100px;
  min-height: 500px;
}

/* Footer */
/*.footer {
  height: 50px;
  padding: 20px 100px 0px 100px;
  background: #e3e3e3;
  font-size: 12px;
}

.footer a {
  color: #000;
}*/

h1 {
  font-size: 20px;
}

h2 {
  font-size: 14px;
}

.footer {
    display: table;

    position: fixed;
    left: 0;
    bottom: 0;
    width: 100%;
    background-color: rgb(61, 61, 61);
    color: white;
    text-align: center;
    height: 50px;

    transition: top 0.3s; /* Transition effect when sliding down (and up) */

}

.footer a {
    color: white;
}

.footer router-link {
  display: table-cell;
  width: 50%;
  padding-top: 15px;
}

.footer p {
  display: table-cell;
  width: 50%;
  padding-top: 15px;
}

/*.footer p {
  display: table-cell;
}*/
</style>
