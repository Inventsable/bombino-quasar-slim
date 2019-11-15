<template>
  <q-page>
    <q-pull-to-refresh @refresh="refresh">
      <quasar-logo />
      <div class="absolute-center">Hello world</div>
    </q-pull-to-refresh>
  </q-page>
</template>

<script>
import { mapGetters, mapActions } from "vuex";

export default {
  components: {
    "quasar-logo": require("src/assets/quasarLogo.vue").default
  },
  data: () => ({}),
  computed: {
    ...mapGetters("settings", ["settings"]),
    app() {
      return this.$root.$children[0];
    },
    size() {
      return this.settings.size;
    }
  },
  async mounted() {
    // await this.app.runCS("init()");
  },
  methods: {
    ...mapActions("settings", ["setSize"]),
    refresh(done) {
      console.log("Refreshing action");
      setTimeout(() => {
        done();
      }, 2000);
    }
  }
};
</script>

<style>
.main-page {
  display: flex;
  justify-content: center;
  align-items: flex-start;
  flex-wrap: wrap;
}
.text-center {
  display: flex;
  justify-content: center;
}

.full-step {
  width: 100%;
  height: 76vh;
}

.q-stepper__header {
  display: none;
}

.q-stepper {
  background: var(--color-bg);
  color: var(--color);
}
</style>
