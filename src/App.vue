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
          <p>
            <code>{{ rule.example }}</code>
          </p>
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
        <a href="https://regexone.com">regexone.com</a>
        <a href="https://man.openbsd.org/OpenBSD-7.6/perlre.1">{{
          currentLanguage === "de"
            ? "Manpage zu Perl Regex"
            : "Perl regex manpage"
        }}</a>
        <a href="https://man.openbsd.org/OpenBSD-7.6/perlretut.1">
          {{
            currentLanguage === "de"
              ? "Tutorial zu Perl Regex"
              : "Perl regex tutorial"
          }}</a
        >
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
          title: { de: "Wortsuche", en: "Word Matching" },
          description: {
            de: 'Nach "Word" suchen',
            en: 'Search for "Word"',
          },
          example: "Word",
        },
        {
          title: {
            de: "Wort am Anfang der Zeile",
            en: "Match the beginning of a line",
          },
          description: {
            de: 'Nach der Zeile, die mit "Word" beginnt, suchen',
            en: 'Search for the line beginning with "Word"',
          },
          example: "^Word",
        },
        {
          title: {
            de: "Wort am Ende der Zeile",
            en: "Match the end of a line",
          },
          description: {
            de: 'Nach der Zeile, die mit "Word" endet, suchen',
            en: 'Search for the line ending with "Word"',
          },
          example: "Word$",
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
