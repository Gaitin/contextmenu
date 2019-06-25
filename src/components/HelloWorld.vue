<template>
  <div class="hello">
    <ul >
      <li v-for="i in 20"  v-superMenu="obj">
        <label >
          <a >haha {{i}}</a>
        </label>
        </li>
    </ul>
  </div>
</template>

<script>
export default {
  name: 'HelloWorld',
  directives: {
    superMenu: {
      bind:  function(el, bind, vNode){},
      inserted: function(el, bind, vNode){
        console.log(el)
        console.log(bind)
        console.log(vNode)
        let menuTop= 0,menuBottom = 0,offset=0
        el.oncontextmenu = function(e){
          console.log(e)
          const bottom = e.view.innerHeight - e.clientY
          let o = document.body;
          let div = document.createElement("div")
          div.id = 'aaa'
          div.style.width = '50px'
          div.style.height = '200px'
          div.style.background = 'blue'
          div.style.position = 'fixed'
          if (bottom < el.clientHeight) {
            menuTop=0
            menuBottom=bottom
          } else {
            menuTop=e.clientY
            menuBottom=0
          }
          offset = e.clientX
          div.innerHTML = 'ccc'
          menuTop&&(div.style.top = menuTop+'px')
          menuBottom&&(div.style.bottom = menuBottom+'px')
          offset&&(div.style.left = offset+'px')
          o.appendChild(div)
        console.log(menuTop,menuBottom,offset)
        }
      },
      update: function(el, bind, vNode){},
      componentUpdated: function(el, bind, vNode){},
      unbind: function(el, bind, vNode){}
    }
  },
  data () {
    return {
      obj: {
        msg:1,
        cc:2
      }
    }
  },
  methods:{
    contextmenu(){}
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>

ul {
  display: flex;
  flex-direction: column;
}
li {
  display: inline-block;
  margin: 0 10px;
  height: 60px;
  border: 1px solid;
}
a {
  color: #42b983;
}
</style>
