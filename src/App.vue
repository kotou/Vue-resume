<template>
  <div id="app" :class="{previewMode: previewMode}">
    <Topbar class="topbar" @preview="preview"></Topbar>
    <main>
      <Editor :resume="resume" class="editor"></Editor>
      <Preview :resume="resume" class="preview"></Preview>
    </main>
    <el-button id="exitPreview" @click="exitPreview">退出预览</el-button>
  </div>
</template>

<script>
  import Topbar from './components/Topbar'
  import Editor from './components/Editor.vue'
  import Preview from './components/Preview'
  export default {
    data() {
      return {
        previewMode: false,
        resume: {
          profile: { name: '', city: '', birth: '' },
          studyExperience: [{ school: '', duration: '', degree: '' }],
          workExperience: [{ company: '', content: '' }],
          projects: [{ name: '', content: '' }],
          awards: [{ name: '' }],
          contacts: { qq: '', wechat: '', email: '', phone: '' }
        }
      }
    },
    methods: {
      preview() {
        this.previewMode = true
      },
      exitPreview() {
        this.previewMode = false
      }
    },
    components: {
      Topbar, Editor, Preview
    }
  }
</script>

<style lang='scss'>
  #app {
    font-family: 'Avenir', Helvetica, Arial, sans-serif;
    -webkit-font-smoothing: antialiased;
    -moz-osx-font-smoothing: grayscale;
    height: 100vh;
    display: flex;
    flex-direction: column;
  }

  .icon {
    width: 1em;
    height: 1em;
    vertical-align: -0.15em;
    fill: currentColor;
    overflow: hidden;
  }

  main {
    display: flex;
    flex: 1;
    background: #ddd;
    .editor {
      width: 40em;
      margin: 16px 8px 16px 16px;
      background: #fff;
      box-shadow: 0 0 5px #5d5d5d;
      border-radius: 3px;
      overflow: hidden;
    }

    .preview {
      flex: 1;
      margin: 16px 16px 16px 8px;
      background: #fff;
      box-shadow: 0 0 5px #5d5d5d;
      border-radius: 3px;
    }
  }
  .previewMode > #topbar {
    display: none;
  }
  .previewMode #editor {
    display: none;
  }
  .previewMode .preview {
    max-width: 800px;
    margin: 32px auto;
  }
  #exitPreview {
    display: none;
  }
  .previewMode #exitPreview {
    display: inline-block;
    position: fixed;
    right: 16px;
    bottom: 16px;
  }
</style>