<template>
    <DocSectionText v-bind="$attrs">
        <p>Loading state can be used <i>loading</i> property.</p>
    </DocSectionText>
    <div class="card flex justify-content-center">
        <MultiSelect placeholder="Loading..." loading class="w-full md:w-20rem"></MultiSelect>
    </div>
    <DocSectionCode :code="code" />
</template>

<script>
export default {
    data() {
        return {
            code: {
                basic: `
<MultiSelect placeholder="Loading..." loading class="w-full md:w-20rem"></MultiSelect>`,
                options: `
<template>
    <div class="card flex justify-content-center">
        <MultiSelect placeholder="Loading..." loading class="w-full md:w-20rem"></MultiSelect>
    </div>
</template>

<script>
<\/script>`,
                composition: `
<template>
    <div class="card flex justify-content-center">
        <MultiSelect placeholder="Loading..." loading class="w-full md:w-20rem"></MultiSelect>
    </div>
</template>

<script setup>
<\/script>`
            }
        };
    }
};
</script>
