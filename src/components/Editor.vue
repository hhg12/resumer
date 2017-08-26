<template>
  <div id="editor">
    <nav>
      <ol>
        <li v-for="(item, index) in resume.config"
           v-bind:class="{active:seleted===item.field}"
          @click="seleted=item.field">
          <svg class="icon" aria-hidden="true">
            <use v-bind:xlink:href="`#icon-${item.icon}`"></use>
          </svg>
        </li>
      </ol>
    </nav>
    <ol class="panels">
      <li v-for="item in resume.config"
        :class="{active: seleted === item.field}"
        >
        <div v-if="resume[item.field] instanceof Array">
          <div v-for="item in resume[item.field]">
            <div class="resumeField" v-for="(value,key) in item">
              <label >{{key}}</label>
              <input type="text" v-model="item[key]">
            </div>
            <hr>
          </div>
        </div>
        <div v-else class="resumeField" v-for="(value,key) in resume[item.field]">
          <label>{{key}}</label>
          <input type="text" v-model="resume[item.field][key]">
        </div>
         
        </li>
    </ol>
  </div>
</template>

<script>
export default {
  name: 'Editor',
  data: function(){
    return {
      seleted: 'profile',
      resume: {
        config: [ 
          {field: 'profile', icon: 'shenfenzhengzhengjian'},
          {field: 'work', icon: 'gongsi'},
          {field: 'education', icon: 'book'},
          {field: 'projects', icon: 'xin'},
          {field: 'awards', icon: 'jiangbei01'},
          {field: 'contacts', icon: '3-copy'}
        ],
        profile: {
          name: '',
          city: '',
          title: ''
        },
        work: [
          {conpany: 'Al', content: '我的第二份工作是'},
          {conpany: 'tx', content: '我的第一份工作是'}
        ],
        education: [
            { school: 'AL', content: '文字' },
            { school: 'TX', content: '文字' },
        ],
        projects: [
          { name: 'project A', content: '文字' },
          { name: 'project B', content: '文字' },
        ],
        awards: [
          { name: 'awards A', content: '文字' },
          { name: 'awards B', content: '文字' },
        ],
        contacts: [
          { contact: 'phone', content: '13812345678' },
          { contact: 'qq', content: '12345678' },
        ]
      }
    }

  }
}
</script>

<style scoped lang="scss">
.icon {
    width: 24px; height: 24px;
    fill: white;
}
#editor {
  color: black;
  min-height: 100px;
  background: #fff;
  box-shadow: 0 1px 3px 0 rgba(0,0,0,0.25);
  display: flex;
  > nav {
    background: black;
    width: 80px;
    > ol > li {
      padding: 8px 0;
      text-align: center;
      &.active {
        background: white;
        > .icon {
          fill: black;
        }
      }
    }
  }
  .panels{
    flex: 1;
    li{
      display: none;
      padding: 24px;
      &.active {
        display: block;
      }
    }
  }
}
.resumeField {
  margin-bottom: 16px;
  > label {
    display: block;
    font-size: 24px;
  }
  > input {
    height: 40px;
    box-shadow: inset 0 1px 3px 0 rgba(0,0,0,0.25);
    width: 100%;
    margin: 16px 0;
  }
}
</style>
