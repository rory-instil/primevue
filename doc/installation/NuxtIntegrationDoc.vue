<template>
    <DocSectionText v-bind="$attrs">
        <p>PrimeVue can easily be used with Nuxt 3 using a custom plugin.</p>

        <h3>nuxt.config.js</h3>
        <p>Open the nuxt configuration file and add the css dependencies. This step is only required when using styled mode and can be ignored in unstyled mode.</p>

        <DocSectionCode :code="code1" hideToggleCode importCode hideCodeSandbox hideStackBlitz />

        <h3>primevue.js</h3>
        <p>Create a file like <i>primevue.js</i> under the plugins directory for the configuration.</p>

        <DocSectionCode :code="code2" hideToggleCode importCode hideCodeSandbox hideStackBlitz />
    </DocSectionText>
</template>

<script>
export default {
    data() {
        return {
            code1: {
                basic: `
export default defineNuxtConfig({
    css: [
        "primevue/resources/themes/lara-light-blue/theme.css"
    ],
	build: {
		transpile: ["primevue"]
	}
})
`
            },
            code2: {
                basic: `
import { defineNuxtPlugin } from "#app";
import PrimeVue from "primevue/config";
import Button from "primevue/button";

export default defineNuxtPlugin((nuxtApp) => {
    nuxtApp.vueApp.use(PrimeVue, { ripple: true });
    nuxtApp.vueApp.component("Button", Button);
    //other components that you need
});
`
            }
        };
    }
};
</script>
