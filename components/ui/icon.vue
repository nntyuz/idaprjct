<template>
  <component :is="name"></component>
</template>

<script>
import bin from '@/components/icons/bin'
import arrowDown from '@/components/icons/arrow-down'
export default {
  components: {
    bin,
    arrowDown
  },
  props: {
    name: String
  }
}
</script>
