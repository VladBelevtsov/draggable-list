<template>
  <div class="hello">
    <h1>Skills</h1>

    <draggable v-model="myArray" ghost-class="ghost" @end="onEnd">
      <transition-group type="transition" name="flip-list">
        <div class="sortable" :id="element.id" v-for="element in myArray" :key="element.id">
          <strong>{{ element.name }}</strong>
          <span>{{ element.id }}</span>
        </div>
      </transition-group>
    </draggable>

    <p><strong>Previos Index: </strong>{{ oldIndex }}</p>
    <p><strong>New Index: </strong>{{ newIndex }}</p>

    <div class="author">
      Made by <a  target="_blank" href="https://www.facebook.com/BielievtsovVlad">Vlad Bielievtsov</a>, source code available on <a target="_blank" href="https://github.com/VladBelevtsov/draggable-list">github</a>
    </div>
  </div>
</template>

<script>
import draggable from 'vuedraggable'
export default {
  name: 'HelloWorld',
  components: {
    draggable
  },
  props: {
    msg: String
  },
  data() {
    return {
      myArray: [
        { name: "Angular", id: 0 },
        { name: "React", id: 1 },
        { name: "Vue", id: 2 },
        { name: "HTML", id: 3 },
        { name: "CSS", id: 4 },
        { name: "JavaScript", id: 5 }
      ],
      oldIndex: '',
      newIndex: ''
    }
  },
  methods: {
    onEnd: function(e) {
      console.log(e);
      this.oldIndex = e.oldIndex;
      this.newIndex = e.newIndex;
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped lang="scss">
h3 {
  margin: 40px 0 0;
  
}

strong {
  display: inline-block;
  
}

.sortable {
  background: #fff;
  padding: 1em;
  cursor: grab;
  margin-bottom: 2px;

  span {
    float: right;
  }
}

.hello .sortable-drag {
  opacity: 0;
}

// .flip-list-move {
//   //transition: transform .5s;
// }

.ghost {
  border-left: 6px solid rgb(0, 183, 255);
  box-shadow: 0 0 5px -1px rgba($color: #000000, $alpha: 0.2);
}

.author {
  padding-bottom: 5rem;
  position: absolute;
  bottom: 0;

  a {
    color: #000;
  }
}
</style>
