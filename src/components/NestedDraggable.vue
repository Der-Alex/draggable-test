<template>
  <draggable
    tag="div"
    class="list"
    group="foo"
    :list="list"
    ghostClass="ghost" dragClass="drag" chosenClass="chosen"
  >
    <div class="list-item" v-for="el in realValue" :key="el.id">
      {{ el.name + '-' + el.id }}
      <nested-draggable :list="el.items"  />
    </div>
  </draggable>
</template>

<script>
import draggable from "vuedraggable";
export default {
  name: "NestedDraggable",
  methods: {
    emitter(value) {
      this.$emit("input", value);
    }
  },
  components: {
    draggable
  },
  computed: {
    dragOptions() {
      return {
        animation: 0,
        group: "description",
        disabled: false,
        ghostClass: "ghost"
      };
    },
    // this.value when input = v-model
    // this.list  when input != v-model
    realValue() {
      return this.value ? this.value : this.list;
    }
  },
  props: {
    list: {
      required: false,
      type: Array,
      default: null
    }
  }
};
</script>
