<script>
import { mergeData } from 'vue-functional-data-merge';

/**
 * Компонент лоадера.
 * Если указано значение true, рендерит вращающуюся иконку.
 * Если указано false, рендерит переданный слот (только одного потомка)
 */
export default {
  name: 'AppLoading',
  functional: true,
  props: {
    value: {
      type: Boolean,
      default: true,
    },
  },
  render(h, context) {
    const { value } = context.props;
    return value
      ? h('app-mdi-icon', mergeData(context.data, {
        class: 'app-loading',
      }), 'loading')
      : context.children[0];
  },
};
</script>

<style lang="sass">
@keyframes appLoadingRotation
  0%
    transform: rotate(0)
  100%
    transform: rotate(360deg)

.app-loading
  animation-name: appLoadingRotation
  animation-duration: .5s
  animation-iteration-count: infinite
  animation-timing-function: linear
</style>
