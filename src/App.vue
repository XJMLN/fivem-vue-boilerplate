<template>
    <div id="app">
    </div>
</template>


<script>

import Nui from './utils/Nui';

export default {
    name: "app",
    components: {
        //component
    },
    data() {
        return {};
    },
    destroyed() {
        window.removeEventListener("message", this.listener);
    },
    mounted() {
        this.listener = window.addEventListener(
          'message',
          event => {
              const element = event.data || event.detail;
              if (this[element.type]) {
                  this[element.type](element);
              }
          },
          false,
        );
    }
}
</script>

<style lang="scss">
</style>