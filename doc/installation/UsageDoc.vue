<template>
    <DocSectionText v-bind="$attrs">
        <p>Each component can be imported individually so that you only bundle what you use. Import path is available in the documentation of the corresponding component.</p>
    </DocSectionText>
    <div class="card flex justify-content-center">
        <Button label="Check" icon="pi pi-check" />
    </div>
    <DocSectionCode :code="code" importCode />
</template>

<script>
export default {
    data() {
        return {
            code: {
                basic: `
import Button from "primevue/button"

const app = createApp(App);
app.component('Button', Button);
`,
                options: `
<template>
    <div class="card flex justify-content-center">
        <Button label="Check" icon="pi pi-check" />
    </div>
</template>`,
                composition: `
<template>
    <div class="card flex justify-content-center">
        <Button label="Check" icon="pi pi-check" />
    </div>
</template>`
            }
        };
    }
};
</script>
