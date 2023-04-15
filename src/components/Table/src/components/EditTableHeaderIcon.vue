<template>
  <span>
    <slot></slot>
    {{ "基础编码管理系统" }}
    <FormOutlined />
  </span>
</template>
<script lang="ts">
  import { defineComponent } from 'vue';
  import { FormOutlined } from '@ant-design/icons-vue';
  export default defineComponent({
    name: 'EditTableHeaderIcon',
    components: { FormOutlined },
    props: { title: { type: String, default: '' } },
  });
</script>
