<template>
  <span :class="klass.tag" :invalid="invalid">
    {{text}}
    <span
      v-if="remove"
      class="hl-click remove"
      @click="remove"
    ></span>
  </span>
</template>
<style scoped>
.tag {
  color: #212121;
  height: 25px;
  line-height: 25px;
  background: #f2f2f2;
  border-radius: 12px;
  padding: 0 10px;
  border: 0;
  font-size: 12px;
  margin: 3px 0;
  position: relative;
}

.tag[invalid] {
  color: #ff7043;
}

.tag[invalid] .remove::after{
  color: #ff7043;
}

.tag:hover .remove{
    display: block;
}
.remove {
    cursor: pointer;
    background-image: linear-gradient(90deg, rgba(242,242,242,0.00) 0%, #f2f2f2 50%);
    display: block;
    width: 30px;
    height: 100%;
    position: absolute;
    right: 0;
    top: 0;
    border-top-right-radius: 12px;
    border-bottom-right-radius: 12px;
    text-align: right;
    margin-right: 7px;
    display: none;
}
.remove:hover::after{
    color: #ff7043;
}
.remove::after{
    color: #c2c2c2;
    content: "\00D7";
}

</style>
<script>
import {str, bool} from 'vuept'


export default {
  props: {
    text: str.required,
    remove: [Function, null],
    invalid: bool.default(false),
  },
  computed: {
    klass() {
      return this.$parent.klass
    }
  }
}
</script>
