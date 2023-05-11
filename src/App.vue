<script>
import axios from "axios";

export default {
  data() {
    return {
      inputText: "",
      translatedText: "",
    };
  },
  methods: {
    async translateText() {
      try {
        const response = await axios.get(
          "https://translate.yandex.net/api/v1.5/tr.json/translate",
          {
            params: {
              key: "trnsl.1.1.20230424T144657Z.4f6d0e13b7ab9120.f4963069dcc7372482aebd09362a90660204fc05",
              text: this.inputText,
              lang: "pt-en", // de português para inglês, mas pode ser alterado para qualquer idioma
            },
          }
        );
        this.translatedText = response.data.text[0];
      } catch (error) {
        console.error(error);
      }
    },
  },
};
</script>

<template>
  <div class="wrapper">
    <input v-model="inputText" type="text" />
    <button @click="translateText">Traduzir</button>
    <textarea v-model="translatedText" readonly></textarea>
  </div>
</template>

<style></style>
