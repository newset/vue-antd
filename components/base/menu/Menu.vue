<template>
<ul 
  :class="className + ' '+ prefixCls + '-' + mode">
  <slot></slot>
</ul>
</template>

<script>
import { defaultProps, oneOf, cx, scrollIntoView } from '../../../utils'
import { getKeyFromChildrenIndex } from './util'
import MenuItem from './MenuItem.vue'

export default {
  props: defaultProps({
    prefixCls: 'ant-menu',
    className: '',
    mode: 'vertical',
    level: 1,
    inlineIndent: 24,
    visible: true,
    focusable: true,
    style: {
      type: Object,
      default () {return {}}
    },
    openSubMenuOnMouseEnter: true,
    closeSubMenuOnMouseLeave: true,
    selectable: true,
    onClick () {},
    onSelect () {},
    onOpen () {},
    onClose () {},
    onDeselect () {},
    defaultSelectedKeys: {
      type: Array,
      default () {return []}
    },
    defaultOpenKeys: {
      type: Array,
      default () {return []}
    }
  }),

  computed: {

  },

  ready () {
    this._mapPropsToChildComponent()
  },

  methods: {
    _mapPropsToChildComponent () {
      this.$children.forEach((child, index) => {
        child.className += ` ${this.prefixCls}-root`
      })
    }
  }
}
</script>
