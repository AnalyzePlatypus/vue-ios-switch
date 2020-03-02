<template>
  <label class="vue-ios-switch">
    <input type="checkbox" v-model="checkboxValue" >
    <span></span>
  </label>
</template>

<script>
export default {
  name: 'Vue-iOSSwitch',
  props: {
    value: {
      required: true,
      type: Boolean
    }
  },
  methods: {
  },
  computed: {
    checkboxValue: {
      get() {
        return this.value;
      },
      set(e) {
        this.$emit("input", e);
      }
    },
    checkmarkDynamicClasses() {
      return this.isChecked ? "is-active" : ""
    }
  }
};
</script>

<!-- Add 'scoped' attribute to limit CSS to this component only -->
<style lang='scss'>

// $span-animate-time: 0.40s;
// $span-animate2-time: 0.25s;

$color-success--4: #48CE5F;;
$color-success--5: rgb(64, 189, 85);

$span-animate-time: 0.30s;
$span-animate2-time: 0.15s;

.vue-ios-switch {
    font-size: 1.5rem;
    display: inline-block;
    position: relative;
    cursor: pointer;
    -webkit-user-select: none;
    -moz-user-select: none;
    -ms-user-select: none;
    user-select: none;
    -webkit-tap-highlight-color: transparent;
}

.vue-ios-switch input {
    opacity: 0;
    position: absolute;
}

.vue-ios-switch input + span {
    position: relative;
    display: inline-block;
    width: 1.65em;
    height: 1em;
    background: white;
    box-shadow: inset 0 0 0 0.0625em #e9e9e9;
    border-radius: 0.5em;
    vertical-align: -0.15em;
    transition: all $span-animate-time cubic-bezier(.17,.67,.43,.98);
}

.vue-ios-switch:active input + span,
.vue-ios-switch input + span:active {
    box-shadow: inset 0 0 0 0.73em #e9e9e9;
}

.vue-ios-switch input + span:after {
    position: absolute;
    display: block;
    content: '';
    width: 0.875em;
    height: 0.875em;
    border-radius: 0.4375em;
    top: 0.0625em;
    left: 0.0625em;
    background: white;
    box-shadow: inset 0 0 0 0.03em rgba(0,0,0,0.1),
                0 0 0.05em rgba(0,0,0,0.05),
                0 0.1em 0.2em rgba(0,0,0,0.2);
    transition: all $span-animate2-time ease-out;
}

.vue-ios-switch:active input + span:after,
.vue-ios-switch input + span:active:after {
    width: 1.15em;
}

.vue-ios-switch input:checked + span {
    box-shadow: inset 0 0 0 0.73em $color-success--4;
}

.vue-ios-switch input:checked + span:after {
    left: 0.7125em;
}

.vue-ios-switch:active input:checked + span:after,
.vue-ios-switch input:checked + span:active:after {
    left: 0.4375em;
}

/* accessibility styles */
.vue-ios-switch input:focus + span:after {
    box-shadow: inset 0 0 0 0.03em rgba(0,0,0,0.15),
                0 0 0.05em rgba(0,0,0,0.08),
                0 0.1em 0.2em rgba(0,0,0,0.3);
    background: #fff;
}

.vue-ios-switch input:focus + span {
    outline: -webkit-focus-ring-color auto 5px;
    box-shadow: inset 0 0 0 0.0625em #dadada;
}

.vue-ios-switch input:focus:checked + span {
    box-shadow: inset 0 0 0 0.73em $color-success--5;
}

/* reset accessibility style on hover */
.vue-ios-switch:hover input:focus + span:after {
    box-shadow: inset 0 0 0 0.03em rgba(0,0,0,0.1),
                0 0 0.05em rgba(0,0,0,0.05),
                0 0.1em 0.2em rgba(0,0,0,0.2);
    background: #fff;
}

.vue-ios-switch:hover input:focus + span {
    box-shadow: inset 0 0 0 0.0625em #e9e9e9;
}

.vue-ios-switch:hover input:focus:checked + span {
    box-shadow: inset 0 0 0 0.73em $color-success--5;
}

</style>

