<template>
    <div>
        <Header></Header>
        <Content></Content>
    </div>
</template>

<script>
import Header from "components/my-header.vue";
import Content from "components/content.vue";

export default {
  components: {
    Header,
    Content
  }
};
</script>

<style lang="less">
</style>
