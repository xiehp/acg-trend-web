<template>
  <div class="Baidutongji" />
</template>

<script>
  export default {
    props: {},
    mounted() {
      const _hmt = _hmt || [];
      (function () {
        const hm = document.createElement("script");
        hm.src = "https://hm.baidu.com/hm.js?623e1d980194c17c40cf9242e300f593";
        const s = document.getElementsByTagName("script")[0];
        s.parentNode.insertBefore(hm, s);
      })();
    },
  }
</script>
