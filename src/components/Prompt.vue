<template>
  <div>
    <DialogCard
      :title="title"
      :actions="actions"
      :handle="handleClick"
      ref="card"
    >
      <v-text-field
        autofocus
        required
        v-model="editedValue"
        :label="text"
        @keypress.enter="$emit('submit', editedValue)"
        @focus="$event.target.select()"
      />
    </DialogCard>
  </div>
</template>

<script>

import Confirmable from 'vuedl/src/mixins/confirmable'
import DialogCard from './DialogCard.vue'

export default {
  components: {
    DialogCard
  },
  layout: 'default',
  mixins: [ Confirmable ],
  props: {
    value: String
  },
  data () {
    return {
      editedValue: this.value
    }
  },
  methods: {
    handleClick (res) {
      this.$emit('submit', this.editedValue)
      return false
    }
  }
}
</script>
