<template>
  <div>
    <Draggable ref="tree" class="mtl-tree" v-model="treeData" treeLine
      ><template #default="{ node, stat }">
        <OpenIcon
          v-if="stat.children.length"
          :open="stat.open"
          class="mtl-mr"
          @click.native="stat.open = !stat.open"
        />
        <input
          class="mtl-checkbox mtl-mr"
          type="checkbox"
          v-model="stat.checked"
        />
        <span class="mtl-ml">{{ node.text }}</span>
      </template></Draggable
    >
  </div>
</template>

<script>
  import { BaseTree, Draggable, pro, OpenIcon } from '@he-tree/vue'
  import '@he-tree/vue/style/default.css'
  import '@he-tree/vue/style/material-design.css'

  export default {
    components: { Draggable, OpenIcon },
    data() {
      return {
        treeData: [
          {
            text: 'Projects',
            children: [
              {
                text: 'Frontend',
                children: [
                  {
                    text: 'Vue',
                    children: [
                      {
                        text: 'Nuxt',
                      },
                    ],
                  },
                  {
                    text: 'React',
                    children: [
                      {
                        text: 'Next',
                      },
                    ],
                  },
                  {
                    text: 'Angular',
                  },
                ],
              },
              {
                text: 'Backend',
              },
            ],
          },
          { text: 'Photos' },
          { text: 'Videos' },
        ],
      }
    },
  }
</script>
<style scoped>
  .actions {
    margin-top: 10px;
    border-top: 1px solid #ccc;
    padding-top: 10px;
  }
  button {
    border: 1px solid #ccc;
    padding: 2px 5px;
    border-radius: 5px;
    margin-right: 8px;
    margin-bottom: 5px;
    font-size: small;
  }
</style>