<template>
  <div id="app">
    <DemoHeader></DemoHeader>
    <main>
      <prop-doc :component="c" :documentation="docs[key]" :key="index" v-for="(c, key, index) in components" v-if="c.name"></prop-doc>
    </main>
  </div>
</template>

<script>
import propDoc from 'propdoc'
import DemoHeader from '@/demo/DemoHeader.vue'
import * as propellant from '@/vue/src'
import * as propellantDocs from '@/vue/docs'

export default {
  name: 'app',
  components: { propDoc, DemoHeader },
  data() {
    return { components: propellant, docs: propellantDocs }
  }
}
</script>

<style lang="scss">
@import "~prpllnt/propellant";
@import "~prpllnt/scss/demo";

body, html {
  background-color: #D5DDE1;
  color: #2B3B43;
  margin: 0;
}

header.docs { flex-direction: row; }

.demo-icon {
  .from-color, .to-color {
    stop-color: #93B29B;
  }
  .center-color {
    fill: #93B29B;
  }
}

main {
  padding: 4.8rem;

  h2 {
    font-weight: 400;
    font-size: 2.4rem;
    line-height: 2.4rem;
    margin: 0;
  }
}

.props {
  .proprow:nth-child(even) {
    background-color: transparentize(#2b3b43, 0.95);
  }

  .proprow {
    display: flex;
    align-items: center;
    justify-content: flex-start;
    padding: 1.6rem 0.8rem;
  }

  .labels {
    padding: 0.8rem;

    > .propcol {
      font-size: 1rem;
      font-weight: 400;
      text-transform: uppercase;
      color: #547484;
    }

    .name span {
      margin-left: 0.4rem;
    }
  }

  .propcol {
    font-size: 1.2rem;
    flex: 1;

    &.notes {
      flex: 2;
    }
  }

  .name {
    font-weight: 600;

    span {}

    &.required span {
      border-bottom: 0.2rem solid transparentize(#CE7780, 0.5);
    }
  }
}

.propcol * {
  display: inline;
}

.propdoc {
  margin-bottom: 12rem;
}

code {
  font-family: "SFMono-Regular", Consolas, "Liberation Mono", Menlo, Courier, monospace;
  background-color: transparentize(#F3C387, 0.5);
  color: #14435A;
  padding: 0.2rem;
}

pre code {
  line-height: 1.8;
  padding: 1.2rem;

  &.labelled, .token & {
    position: relative;
    margin-bottom: 2rem;

    &:after {
      content: attr(data-lang);
      font-size: 0.8rem;
      color: #CE7780;
      font-weight: 600;
      font-family: $base-font-family;
      position: absolute;
      right: 1.2rem;
      bottom: -2rem;
    }
  }
}

.use, .props {
  margin: 2.8rem 0;
}

.token pre {
  margin: 0;
}

.use {
  display: grid;
  grid-template-columns: repeat(2, 1fr);
  grid-gap: 2.8rem;
}

</style>
