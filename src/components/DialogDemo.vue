<template>
  <div>Dialog</div>
  <h1>示例1</h1>
    <Button @click="toggle">toggle</Button>
    <Dialog v-model:visible="x" :closeOnClickOverlay="false" :ok="f1" :cancel="f2">
      <template v-slot:content>
        <strong>hi</strong>
        <div>hi2</div>
      </template>
      <template v-slot:title>
        <strong>加粗的标题</strong>
      </template>
    </Dialog>
  <h1>示例2</h1>
  <Button @click="showDialog">show</Button>
</template>

<script lang="ts">
import Dialog from "../lib/Dialog.vue";
import Button from "../lib/Button.vue";
import {openDialog} from "../lib/openDialog";
import {h, ref} from "vue";

export default {
  name: "DialogDemo",
  components: {Button, Dialog},
  setup() {
    const x = ref(false)
    const toggle = () => {
      x.value = !x.value
    }
    const f1 = () => {
      return false
    }
    const f2 = () => {
    }
    const showDialog = () => {
      openDialog({
        title: h('strong',{},'标题'),
        content:'你好',
        ok(){
        },
        cancel(){
        }
      })
    }
    return {x, toggle, f1, f2, showDialog}
  }
}
</script>

<style scoped>

</style>