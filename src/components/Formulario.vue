<template>
  <div class="box">
    <div class="columns">
      <div
        class="column is-8"
        role="form"
        aria-label="Formulário para criação de uma nova tarefa"
      >
        <input
          type="text"
          class="input"
          placeholder="Qual tarefa você deseja iniciar?"
        />
      </div>
      <div class="column">
        <div
          class="is-flex is-align-items-center is-justify-content-space-between"
        >
          <section>
            <strong>{{ tempoFormatado }}</strong>
          </section>
          <button class="button" @click="iniciar">
            <span class="icon">
              <i class="fas fa-play"></i>
            </span>
            <span>Play</span>
          </button>
          <button class="button" @click="finalizar">
            <span class="icon">
              <i class="fas fa-stop"></i>
            </span>
            <span>Stop</span>
          </button>
        </div>
      </div>
    </div>
  </div>
</template>

<script lang="ts">
import { defineComponent } from "vue";
export default defineComponent({
  name: "Formulario-vue",
  data() {
    return {
      tempo: 0,
      cronometro: 0,
    };
  },
  computed: {
    tempoFormatado(): string {
      return new Date(this.tempo * 1000).toISOString().substr(11, 8);
    },
  },
  methods: {
    iniciar() {
      this.cronometro = setInterval(() => {
        this.tempo++;
      }, 1000);
    },
    finalizar() {
      clearInterval(this.cronometro);
    },
  },
});
</script>
