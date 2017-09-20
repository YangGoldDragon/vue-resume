<template>
  <div id="editor">
    <ul class="tab">
      <li v-for="i in [0,1,2,3,4,5]" v-bind:class="{active: currentTab === i}" v-on:click="currentTab = i">
        <svg class="icon" aria-hidden="true">
          <use v-bind:xlink:href="'#icon-'+icons[i]+''"></use>
        </svg>
      </li>
    </ul>
    <ul class="content">
      <li v-bind:class="{active: currentTab === 0}">tab1</li>
      <li v-bind:class="{active: currentTab === 1}">tab2</li>
      <li v-bind:class="{active: currentTab === 2}">tab3</li>
      <li v-bind:class="{active: currentTab === 3}">tab4</li>
      <li v-bind:class="{active: currentTab === 4}">tab5</li>
      <li v-bind:class="{active: currentTab === 5}">tab6</li>
    </ul>
  </div>
</template>

<style lang="scss">
  #editor{
    display: flex;
    .tab{
      width: 25%;
      height: 100%;
      text-align: center;
      border-right: 1px solid rgb(68, 68, 68);
      li{
        border-bottom: 1px solid rgb(68, 68, 68);
        height: calc(100% / 6);
        display: flex;
        align-items: center;
        justify-content: center;
        &:last-child{
           border: none;
        }
        &.active{
           background: #13ce66;
           .icon{
             fill: white;
           }
        }
      }
    }

    .content{
      width: 75%;
      height: 100%;
      li{
        display: none;
        &.active{
          display: block;
        }
      }
    }
  }

  .icon {
    width: 4em; height: 4em;
    vertical-align: -0.15em;
    fill: #373737;
    overflow: hidden;
  }
</style>

<script>
  export default {
    data(){
      return {
        currentTab: 0,
        icons: ['shenfenzheng', 'work', 'book', 'heart', 'jiangbei', 'phone']
      }
    }
  }
</script>
