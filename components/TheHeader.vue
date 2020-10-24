<template>
  <header class="header">
    <nav>
      <div class="toolBar">
        <a href="/" class="title">NectoJ.io</a>
        <a href="/blog/posts">Posts</a>
        <a href="/blog/tags/programming">Programming</a>
        <!-- <a href="">Random</a> -->
        <a href="https://github.com/SemiShogun">Github</a>
      </div>
    </nav>
  </header>
</template>

<script>
export default {};
</script>

<style scoped>
.header {
  display: flex;
  justify-content: flex-start;
  padding: 30px 0px 15px 0px;
  flex-shrink: 0;
}

.toolBar > a,
.toolbar > a:link,
.toolbar > a:visited,
.toolbar > a:hover,
.toolbar > a:focus,
.toolbar > a:active {
  text-decoration: none;
  padding: 0px 20px 0px 20px;
  color: #6631ff;
}

.title {
  font-size: 2em;
}
</style>