<template>
  <section key="emojis-box" class="box">
    <nav class="level">
      <div class="level-left">
        <div class="level-item">
        </div>
      </div>
      <div class="level-right">
        <p class="level-item">
          <button @click="emitCloseModal" class="delete is-large"></button>
        </p>
      </div>
    </nav>
    <div v-for="(category, index) in emojiData" :key="index" class="section">
      <div class="title is-6">{{ category.group }}</div>
      <div class="columns is-multiline">
        <div v-for="(emoji, i) in category.emojis" :key="index+i" class="column is-mobile is-narrow" @click="emitAddEmoji(emoji.emoji)">
          {{ emoji.emoji }}
        </div>
      </div>
    </div>
  </section>
</template>

<script>
import emojiData from '~/assets/chat/emojiByGroup.js'
export default {
  data: () => ({
    emojiData,
  }),
  methods: {
    emitCloseModal() {
      this.$emit('closeModal')
    },
    emitAddEmoji(emoji) {
      this.$emit("addEmoji", emoji)
    }
  }
}
</script>