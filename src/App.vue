<template>
  <div id="app">
    <div class="l">
      <nested-draggable group="foo" :list="list1" />
      </div>
    <div class="r">
      <draggable class="list" group="foo" :list="list2" ghostClass="ghost" dragClass="drag" chosenClass="chosen" >
        <div
          class="list-item"
          v-for="(element) in list2"
          :key="element.id"
        >
          {{ element.name + ' - ' + element.id }}
        </div>
      </draggable>
    </div>
  </div>
</template>

<script>
import draggable from 'vuedraggable';
import NestedDraggable from '@/components/NestedDraggable.vue';

export default {
  name: 'App',
  components: {
    draggable,
    NestedDraggable
  },
  data() {
    return {
      list2: [
        {
          id: 101,
          name: 'a',
          items: []
        },
        {
          id: 102,
          name: 'b',
          items: [
            {
              id: 121,
              name: 'b-a',
              items: []
            },
          ]
        },
        {
          id: 103,
          name: 'c',
          items: []
        },
      ],
      list1: [
        {
          id: 1,
          name: 'a',
          items: []
        },
        {
          id: 2,
          name: 'b',
          items: [
            {
              id: 21,
              name: 'b-a',
              items: []
            },
          ]
        },
        {
          id: 3,
          name: 'c',
          items: []
        },
      ]
    };
  }
}
</script>

<style lang="scss">
* {
  box-sizing: border-box;
}
#app {
  font-family:  sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  display: grid;
  grid-template-columns: 1fr 1fr;
}
.l, .r {
  min-height: 100px;
  background-color: #eee;
  border: 1px solid #ddd;
}
.list {
  padding: 40px;
  background: #ddd;
}

.list-item {
  border: 1px dotted #999;
  padding: 4px;
  background: #ccc;
  > .list {
    padding: 40px;
    background: #ddd
  }
}

.chosen {
  height: 29px;
  background-color: #bbb;
  overflow: hidden;
    -webkit-touch-callout: none; /* iOS Safari */
    -webkit-user-select: none; /* Safari */
     -khtml-user-select: none; /* Konqueror HTML */
       -moz-user-select: none; /* Old versions of Firefox */
        -ms-user-select: none; /* Internet Explorer/Edge */
            user-select: none;
}
.ghost {
  opacity: 0.6;
}
</style>
