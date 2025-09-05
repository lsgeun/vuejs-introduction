<script>
import FirstChild from '@/components/FirstChild.vue';
import SecondChild from '@/components/SecondChild.vue';
export default {
  components: {
    FirstChild,
    SecondChild,
  },
  data() {
    return {
      visible: true,
    }
  },
  // 뷰의 라이프사이클 훅
  beforeCreate() {
    console.log('beforeCreate');
  },
  created() {
    console.log('created');
    setTimeout(() => {
      this.visible = false;
    }, 3000);
  },
  beforeMount() {
    console.log('beforeMount');
  },
  mounted() {
    console.log('mounted');
    const domEl = this.$refs.domEl;
    const text = domEl.innerText;
    console.log(text);
    
    console.log(`메서드 호출 전: ${this.$refs.child.num}`);
    console.log(`메서드 호출 전: ${this.$refs.child.doubleNum}`);
    
    setTimeout(() => {
      this.$refs.child.increment();
      console.log(`메서드 호출 후: ${this.$refs.child.num}`);
      console.log(`메서드 호출 후: ${this.$refs.child.doubleNum}`);
    }, 1000);
  },
  beforeUpdate() {
    console.log('beforeUpdate');
  },
  updated() {
    console.log('updated');
  },
  beforeUnmount() {
    console.log('beforeUnmount');
  },
  unmounted() {
    console.log('unmounted');
  },
}

</script>
<template>
  <FirstChild v-if="visible" ref="child" />
  <!-- <SecondChild /> -->
  <hr>
  <h1 ref="domEl">h1 태그</h1>
  <hr>
</template>

<style scoped>
h1,
p {
  color: orange !important;
}
</style>
