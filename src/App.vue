<template>
  <div id="app">
    <gallery />
  </div>
</template>

<script>
import Gallery from '@/views/Gallery.vue';

export default {
  name: 'App',
  components: {
    Gallery
  }
}
</script>

<style>
/* CSS Reset */
body, div, span, object, iframe, input, h1, h2, h3, h4, h5, h6, p, pre, a, acronym, address, code, del, em, font, img, ins, strong, b, i, dl, dt, dd, ol, ul, li, fieldset, form, label, table, tbody, tfoot, thead, tr, th, td {
    padding: 0;
    margin: 0; }
  
  table {
    border-collapse: collapse;
    border-spacing: 0; }
  
  ins {
    text-decoration: none; }
  
  del {
    text-decoration: line-through; }
  
  input, select {
    vertical-align: middle; }
  
  input, textarea, select {
    font: 12px/1.5 "microsoft yahei", Arial, sans-serif; }
  
  fieldset, img {
    border: 0; }
  
  address, code, th, em {
    font-style: normal; }
  
  ol, ul {
    list-style: none; }
  
  h1, h2, h3, h4, h5, h6 {
    font-size: 100%; }
  
  /* bass css */
  body {
    position: relative;
    margin: 0 auto;
    font: 14px/1.5 "microsoft yahei", Arial, sans-serif;
    color: #666;
    line-height: 1.5;
    background: #f5f5f5; }
    body.ox {
      overflow-x: hidden; }
    body.oh {
      overflow: hidden; }
  
  body.bg {
    background-color: #f2f2f2; }
  
  html, body {
    height: 100%; }
  
  html.ovh {
    height: 100%;
    overflow: hidden; }
    html.ovh body {
      height: 100%;
      overflow: hidden; }
  
  .wrapper {
    margin: 0 auto;
    width: 1412px; }
  
  .clearfix:after {
    content: "";
    height: 0;
    visibility: hidden;
    display: block;
    clear: both; }
  
  .clearfix {
    zoom: 1; }
  
  .clear {
    clear: both; }
  
  a {
    text-decoration: none;
    outline: none;
    cursor: pointer; }
  
  .absolute {
    position: absolute; }
  
  .relative {
    position: relative; }
  
  .center {
    text-align: center; }
  
  .fl {
    float: left; }
  
  .fr {
    float: right; }
  
  .transparent {
    opacity: 0; }
  
  .hide {
    display: none !important; }

#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
}
</style>
