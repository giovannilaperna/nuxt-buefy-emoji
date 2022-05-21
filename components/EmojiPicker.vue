<template>
  <section key="emojis-box" class="box">
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
    emitAddEmoji(emoji) {
      this.$emit("addEmoji", emoji)
    }
  }
}
</script>