<template>
  <button
    class="xst-button"
    :disabled="buttonDisabled || loading"
    :autofocus="autofocus"
    :type="nativeType"
    :class="[type ? 'xst-button--' + type : '',buttonSize ? 'xst-button--' + buttonSize : '',
      {
        'is-disabled': buttonDisabled,
        'is-loading': loading,
        'is-plain': plain,
        'is-round': round,
        'is-circle': circle
      }
    ]"
  >
    <i class="xst-icon-loading" v-if="loading"></i>
    <i :class="icon" v-if="icon&&!loading"></i>
    <span v-if="$slots.default">
      <slot></slot>
    </span>
  </button>
</template>
<script>
  export default {
    name: 'xst-button',
    inject: {
      elForm: {
        default:
          ''
      },
      elFormItem: {
        default:
          ''
      }
    },
    props: {
      type: {
        type: String,
        default:
          'default'
      },
      size: String,
      icon: {
        type: String,
        default:
          ''
      },
      nativeType: {
        type: String,
        default:
          'button'
      },
      loading: Boolean,
      disabled: Boolean,
      plain: Boolean,
      autofocus: Boolean,
      round: Boolean,
      circle: Boolean
    },
    computed: {
      _elFormItemSize() {
        return (this.elFormItem || {}).elFormItemSize;
      },
      buttonSize() {
        return this.size || this._elFormItemSize || (this.$ELEMENT || {}).size;
      },
      buttonDisabled() {
        return this.disabled || (this.elForm || {}).disabled;
      }
    },

    methods: {
    }
  };
</script>
