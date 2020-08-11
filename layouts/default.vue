<template>
  <main>
    <nuxt class="main-view mtx" />
  </main>
</template>


<script>

import { mapActions, mapGetters } from "vuex";

export default {
};
</script>

<style lang="css">

:root {
  --text: black;
  --link: #be7a0b;
  --button: #753751;
  --background: #fff;
}

html,body,p,ol,ul,li,dl,dt,dd,blockquote,figure,fieldset,legend,textarea,pre,iframe,hr,h1,h2,h3,h4,h5,h6{margin:0;padding:0}h1,h2,h3,h4,h5,h6{font-size:100%;font-weight:normal}ul{list-style:none}button,input,select,textarea{margin:0}html{box-sizing:border-box}*,*:before,*:after{box-sizing:inherit}iframe{border:0}table{border-collapse:collapse;border-spacing:0}td,th{padding:0;text-align:left}

body {
  background: var(--background);
  color: var(--text);
  font-size: 24px;
  font-family: monospace;
}

a {
  letter-spacing: 3px;
  text-decoration: none;
  color: var(--link);
}

a:focus {
    outline:0;
}

a:active,
a:hover {
    outline: 0;
    opacity: 0.7;
}

h1 {
  font-size: 48px;
}

h2 {
  font-size: 22px;
}

button {
  padding: 24px;
  outline: none;
  border-radius: 3px;
  border: 0px;
  background: var(--button);
  color: white;
  font-family: monospace;
  transition: 0.4s all;
}

input, textarea {
  padding: 24px;
  width: 100%;
  border-radius: 3px;
  outline: none;
  border: 0px;
  background: rgba(0, 0, 0, 0.05);
  color: black;
  font-family: monospace;
  transition: 0.4s all;
}

input:focus, textarea:focus {
  background: rgba(0, 0, 0, 0.1);
}

textarea {
  resize: vertical;
}

button[disabled] {
  background: rgba(164, 55, 116, 0.04);
}

button:hover:not(:disabled) {
  transform: scale(1.15);
  cursor: pointer;
  box-shadow: inset 0 0 8px 32px rgba(0, 0, 0, 0.05);
}

button::-moz-focus-inner {
  border: 0;
}

.gutter {
  margin: auto;
  width: 50%;
}

.row {
  width: 100%;
  display: inline-block;
}

.flex-wrapper {
  display: flex;
}

.flex-grid {
  display: flex;
  flex-wrap: wrap;
  column-gap: 8px;
  row-gap: 8px;
}

.flex-grid-item {
  flex-grow: 1;
}

.c100 {
  width: 100%;
}

.c75 {
  width: 75%;
}

.c50 {
  width: 50%;
}

.c25 {
  width: 25%;
}

.mt {
  margin-top: 16px;
}

.mb {
  margin-bottom: 16px;
}

.mtx {
  margin-top: 128px;
}

.text-center {
  text-align: center;
}

</style>
