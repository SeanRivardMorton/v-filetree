<template>
    <div>
        <div :class="{bold: isFolder}" @click="toggle" @dblclick="changeType">
            <span>
                <v-icon v-if="isFolder && open" class="mr-2">folder_open</v-icon>
                <v-icon v-else-if="isFolder && !open" class="mr-2">folder</v-icon>
                <v-icon v-else class="mr-2">insert_drive_file</v-icon>
                <span class="regular">{{ model.name }}</span>
            </span>
        </div>
        <ul v-show="open" v-if="isFolder">
            <masv-file-tree class="item" v-for="(model, index) in model.children" :key="index" :model="model">
            </masv-file-tree>
            <v-icon class="add" @click="addChild">create_new_folder</v-icon>
        </ul>
    </div>
</template>

<script lang="ts">
import Component from 'nuxt-class-component';
import Vue from 'vue';

@Component({
  props: {
    model: Object
  }
})
export default class MasvFileTree extends Vue {
  model;
  open = false;

  get isFolder() {
    return this.model.children && this.model.children.length;
  }

  toggle() {
    if (this.isFolder) {
      this.open = !this.open;
    }
  }

  changeType() {
    if (!this.isFolder) {
      Vue.set(this.model, 'children', []);
      this.addChild();
      this.open = true;
    }
  }

  addChild() {
    this.model.children.push({
      name: 'new stuff'
    });
  }
}
</script>

<style scoped>
ul {
  padding-left: 1em;
  line-height: 1.5em;
  list-style-type: dot;
}
</style>
