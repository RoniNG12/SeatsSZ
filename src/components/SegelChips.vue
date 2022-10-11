<template>
    <div class="mx-auto d-flex justify-center justify-space-around align-center">
        <slot/>
        <div class="d-flex justify-space-between justify-center"
>
    <v-card 
    >
      <v-card-text>
        <v-chip-group
          v-model="selection"
          column
          active-class="primary--text"
        >
          <draggable v-model="tags" @start="dragStart" @end="dragEnd">
            <v-chip v-for="(tag, i) in tags" :key="i" draggable :color="tag.status==='wrong'?'':'green'">
              {{ tag.name }}
            </v-chip>
          </draggable>
        </v-chip-group>
      </v-card-text>
    </v-card>
   
  </div>
 
    </div>
  
</template>

<script>
import draggable from 'vuedraggable';
export default {
  name: 'App',
props: {
    tags: Array
},
  components: {
    draggable
  },
  data: () => ({
    selection: null,
    currentTag: null,
    
  }),
  methods: {
    dragStart() {
      if (this.tags[this.selection]) this.currentTag = this.tags[this.selection].name;
      else this.currentTag = null;
    },
    dragEnd() {
      var self = this;
      if (this.currentTag) {
        this.tags.forEach((x, i) => {
          if (x.name === self.currentTag) self.selection = i;
        });  
      }
      this.$emit('update:tags',this.tags)
    },
   
  },

};
</script>

<style scoped>

</style>