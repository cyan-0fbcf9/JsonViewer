<template>
  <div v-if="show_sidebar" class="form-group p-0">
    <label for="json-text">JSONファイルを入力</label>
    <textarea
      class="p-2 rounded"
      name="text"
      id="json-text"
      rows="3"
      v-model="textarea_data"
      @keypress.enter.ctrl="on_text_enter"
    ></textarea>
    <input
      class="my-1 rounded input-enter my-button"
      type="submit"
      value="ENTER"
      @click="on_text_enter"
    />
  </div>
  <div v-else class="form-icon">
    <button @click="$emit('click-icon')"><i class="far fa-keyboard"></i></button>
  </div>
</template>

<script>
import JsonManager from '~/plugins/json_manager.js'

export default {
  data() {
    return {
      textarea_data: ''
    }
  },
  props: {
    show_sidebar: Boolean,
  },
  methods: {
    on_text_enter() {
      this.$emit('reset')
      const data = JsonManager.text_to_json(this.textarea_data)
      console.log(data)
      if (data != null) {
        this.$store.commit('json_data/updateData', data)
      } else {
        alert('JSONデータの形式が正しくありません')
      }
    }
  }
}
</script>

<style lang="scss">
#json-text {
  border: 2px solid #0fbcf9;
}
.input-enter {
  font-family: var(--app-font-rounded);
  font-weight: bold;
}
</style>

<style lang="scss" scope>
label {
  color: grey;
}

textarea {
  width: 100%;
  resize: vertical;
}

input {
  padding: 0.3rem 1.5rem;
  background-color: #0fbcf9;
  border: 0px solid white;
  color: white;
  transition: all 0.3s ease-out;

  &:hover {
    box-shadow: 0px 0px 10px #0fbaf950;
  }
}
</style>