<template>
  <div id="editor">
    <nav>
      <ol>
        <li v-for="i in [0,1,2,3,4,5]"
           v-bind:class="{active:visibleItem===i}"
          @click="visibleItem=i">
          <svg class="icon" aria-hidden="true">
            <use v-bind:xlink:href="`#icon-${icons[i]}`"></use>
          </svg>
        </li>
      </ol>
    </nav>
    <ol class="panels">
      <li v-bind:class="{active:visibleItem===0}">tab1</li>
      <li v-bind:class="{active:visibleItem===1}">tab2</li>
      <li v-bind:class="{active:visibleItem===2}">tab3</li>
      <li v-bind:class="{active:visibleItem===3}">tab4</li>
      <li v-bind:class="{active:visibleItem===4}">tab5</li>
      <li v-bind:class="{active:visibleItem===5}">tab6</li>
    </ol>
  </div>
</template>

<script>
export default {
  name: 'Editor',
  data: function(){
    return {
      visibleItem: 0,
      icons: ['shenfenzhengzhengjian','gongsi','book','xin','jiangbei01','3-copy']

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
  color: red;
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
  .panels li{
    display: none;
    &.active {
      display: block;
    }
  }
}
</style>
