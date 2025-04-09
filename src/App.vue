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
        {
          title: {
            de: "Zeichen als Zeichen und nicht als regexveränderung nutzen",
            en: "Escaping characters",
          },
          description: {
            de: 'Nach "Word$" suchen',
            en: 'Search for "Word$"',
          },
          example: "Word\\$",
        },
        {
          title: {
            de: "Wildcards",
            en: "wildcards",
          },
          description: {
            de: 'Nach "Wora", "Worb", "Worc" usw. , "Wor1", "Wor2", "Wor3" usw suchen',
            en: 'Search for "Wora", "Worb", "Worc" etc. , "Wor1", "Wor2", "Wor3" etc',
          },
          example: "Wor.",
        },
        {
          title: {
            de: "Nach einem Wort in mehreren Variationen suchen",
            en: "Matching multiple letters",
          },
          description: {
            de: 'Nur nach "Wora" und "Worb" suchen',
            en: 'Search only for "Wora" and "Worb"',
          },
          example: "Wor[ab]",
        },
        {
          title: {
            de: "Repetition von Matches (0 oder mehr mal)",
            en: "repetition of matches (0 or more times)",
          },
          description: {
            de: 'Nach Wort suchen, das mit "Wor" beginnt und danach nur noch aus 0 oder mehreren a oder b besteht (z.B Wor, Woraaaa Worabab, Worbaba, Woraabb, Worbbaa), suchen',
            en: 'Search for a word which begins with "Wor" and continues only with 0 or more  a or b (ex. Wor, Woraaaa, Worbbbb, Worabab, Worbaba, Woraabb, Worbbaa)',
          },
          example: "Wor[ab]*",
        },
        {
          title: {
            de: "Repetition von Matches (1 oder mehr mal)",
            en: "repetition of matches (1 or more times)",
          },
          description: {
            de: 'Nach Wort suchen, das mit "Wor" beginnt und danach nur noch aus 1 oder mehreren a oder b besteht (z.B Woraaaa Worabab, Worbaba, Woraabb, Worbbaa), suchen',
            en: 'Search for a word which begins with "Wor" and continues only with 1 or more  a or b (ex. Woraaaa, Worbbbb, Worabab, Worbaba, Woraabb, Worbbaa)',
          },
          example: "Wor[ab]+",
        },
        {
          title: {
            de: "Inversion",
            en: "inversion",
          },
          description: {
            de: "Nach Zeile suchen, das NICHT a oder b beinhaltet, suchen",
            en: "Search for a Line which does NOT include a or b",
          },
          example: "[^ab]",
        },
        {
          title: {
            de: "Mehrere Begriffe gleichzeitig suchen",
            en: "Search multiple words at the same time",
          },
          description: {
            de: 'Sowohl nach "Word" wie auch nach "asdf" suchen',
            en: 'Search for "Word" and for "asdf" at the same time',
          },
          example: "(Word|asdf)",
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
