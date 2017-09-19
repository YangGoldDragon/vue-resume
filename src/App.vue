<template>
  <div id="app">
    <header>
      <Topbar class="Topbar"/>
    </header>
    <main>
      <Editor class="Editor"/>
      <Preview class="Preview"/>
    </main>
  </div>
</template>

<script>
import Topbar from './components/Topbar'
import Editor from './components/Editor'
import Preview from './components/Preview'
export default {
  name: 'app',
  components: {
    Topbar, Editor, Preview
  }
}
</script>

<style lang="scss">
  html, body, #app{
    height: 100%;
    overflow: hidden;
  }

  #app{
    display: flex;
    flex-direction: column;
  }

  header{
    background: rgba(55, 55, 55, 1);
    color: white;
  }

  main{
    display: flex;
    flex: 1;
    .Editor{
      width: 30%;
      color: rgba(55, 55, 55, 1);
    }

    .Preview{
      width: 70%;
      color: rgba(55, 55, 55, 1);

    }
  }
</style>
