<template>
  <div id="app" :style="{ backgroundColor: backgroundColor }">
    <header>
      <h1>{{ currentLanguage === "de" ? "Regex Regeln" : "Regex Rules" }}</h1>
      <button @click="toggleLanguage">
        {{ currentLanguage === "de" ? "Englisch" : "Deutsch" }}
      </button>
    </header>
    <main>
      <ul>
        <li v-for="(rule, index) in rules" :key="index">
          <h2>{{ rule.title[currentLanguage] }}</h2>
          <p>{{ rule.description[currentLanguage] }}</p>
          <code>{{ rule.example }}</code>
        </li>
      </ul>
    </main>
    <footer>
      <p>
        {{
          currentLanguage === "de"
            ? "Informationen von: "
            : "Informations from: "
        }}
        <a href="https://man.openbsd.org/re_format.7">Manpage zu Regex</a>
      </p>
    </footer>
  </div>
</template>

<script>
export default {
  data() {
    return {
      currentLanguage: "de",
      rules: [
        {
          title: { de: "Regel 1", en: "Rule 1" },
          description: {
            de: "Beschreibung für Regel 1",
            en: "Description for Rule 1",
          },
          example: "Beispiel für Regel 1",
        },
      ],
    };
  },
  methods: {
    toggleLanguage() {
      this.currentLanguage = this.currentLanguage === "de" ? "en" : "de";
    },
  },
};
</script>
