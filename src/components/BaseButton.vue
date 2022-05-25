<template>
    <button class="button" @click="wasClicked" :disabled="wasDesabled">
        <span class="icon">
            <i :class="buttonIcon"></i>
        </span>
        <span>{{buttonName}}</span>
    </button>
</template>

<script lang="ts">
import { defineComponent } from "vue";

export default defineComponent({
  name: 'BaseButton',
  emits: ['wasClicked'],
  props:{
      wasDesabled: {
          type: Boolean
      },
      buttonIcon: {
          type: String,
          required: true
      },
      buttonName:{
          type: String,
          required: true
      },
  },
  methods:{
      wasClicked():void{
          this.$emit('wasClicked')
      }
  }
})
</script>