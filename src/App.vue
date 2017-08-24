<template>
  <div id="app">
    <div class="page">
      <header>
        <Topbar />    
      </header>  
      <main>
        <Editor />
        <Preview />
      </main>

    </div>
       
  </div>
</template>

<script >
import Topbar from './components/Topbar'
import Editor from './components/Editor'
import Preview from './components/Preview'

export default {
  name: 'App',
  components: {     //当前目录下的组件
    Topbar,Editor,Preview
  },
  data: function(){
    return {
      text: '你好'
    }
  }
}
</script>

<style lang="scss">
.page {
  min-width: 1024px;
  max-width: 1440px;
  display: flex;
  flex-direction: column;
  height: 100vh;
  background: #EAEBEC;
  > main {
    display: flex;
    flex: 1;
    justify-content: space-between;
    margin-top: 16px;
    margin-bottom: 16px;
    padding: 0 16px;
    align-self: center;
    width: 100%;
  }
}

#editor {
  width: 30%;
  border-radius: 3px;
  overflow: hidden;
}
#preview {
  flex: 1;
  margin-left: 16px;
  border-radius: 3px;
  overflow: hidden;
}

</style>
