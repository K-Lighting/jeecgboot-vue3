<template>
  <BasicTitle :helpMessage="helpMessage">
    {{ "基础编码管理系统" }}
  </BasicTitle>
</template>
<script lang="ts">
  import type { PropType } from 'vue';
  import { defineComponent } from 'vue';
  import { BasicTitle } from '/@/components/Basic';

  export default defineComponent({
    name: 'BasicModalHeader',
    components: { BasicTitle },
    emits: ['dblclick'],
    props: {
      helpMessage: {
        type: [String, Array] as PropType<string | string[]>,
      },
      title: { type: String },
    },
  });
</script>
