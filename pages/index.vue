<template>
  <section>
    <div class="field">
      <div class="control has-icons-right">
        <textarea v-model="text" ref="ta" class="textarea"></textarea>
        <span class="icon is-right">
          <i @click="activateModal" class="clickable-icon mdi mdi-emoticon mdi-24px"></i>
        </span>
      </div>
    </div>
    <b-modal v-model="isModalActive" :width="640" scroll="keep">
      <emoji-picker @addEmoji="addEmoji" />
    </b-modal>
  </section>
</template>

<script>
  export default {
    data: () => ({
      text: '',
      isModalActive: false,
      cursorStart: 0,
      cursorEnd: 0 
    }),
    methods: {
      activateModal () {
        this.isModalActive = true
        this.cursorStart = this.$refs.ta.selectionStart
        this.cursorEnd = this.$refs.ta.selectionEnd
      },
      addEmoji (emoji) {
        const left = this.text.substring(0, this.cursorStart)
        const right = this.text.substring(this.cursorEnd, this.text.length)
        this.text = left + emoji + right
        this.$refs.ta.focus()
        this.isModalActive = false
      },
    }
  }
</script>

<style>
.clickable-icon {
  pointer-events: all;
  cursor:pointer
}
</style>

