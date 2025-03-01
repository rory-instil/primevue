<template>
    <DocSectionText v-bind="$attrs">
        <p>Indicators can be placed at four different sides using the <i>indicatorsPosition</i> property. In addition, enabling <i>showIndicatorsOnItem</i> moves the indicators inside the image section.</p>
    </DocSectionText>
    <div class="card">
        <div class="flex flex-wrap gap-3 mb-5">
            <div v-for="option in positionOptions" :key="option.label" class="flex align-items-center">
                <RadioButton v-model="position" :inputId="option.label" name="option" :value="option.value" />
                <label :for="option.label" class="ml-2"> {{ option.label }} </label>
            </div>
        </div>
        <div class="flex align-items-center mb-5">
            <Checkbox v-model="inside" inputId="inside_cbox" :binary="true"></Checkbox>
            <label for="inside_cbox" class="ml-2"> Inside </label>
        </div>
        <Galleria :value="images" :numVisible="5" containerStyle="max-width: 640px" :showThumbnails="false" :showIndicators="true" :changeItemOnIndicatorHover="true" :showIndicatorsOnItem="inside" :indicatorsPosition="position">
            <template #item="slotProps">
                <img :src="slotProps.item.itemImageSrc" :alt="slotProps.item.alt" style="width: 100%; display: block" />
            </template>
        </Galleria>
    </div>
    <DocSectionCode :code="code" :service="['PhotoService']" />
</template>

<script>
import { PhotoService } from '@/service/PhotoService';

export default {
    data() {
        return {
            images: null,
            inside: false,
            position: 'bottom',
            positionOptions: [
                {
                    label: 'Bottom',
                    value: 'bottom'
                },
                {
                    label: 'Top',
                    value: 'top'
                },
                {
                    label: 'Left',
                    value: 'left'
                },
                {
                    label: 'Right',
                    value: 'right'
                }
            ],
            code: {
                basic: `
<Galleria :value="images" :numVisible="5" containerStyle="max-width: 640px" :showThumbnails="false"
    :showIndicators="true" :changeItemOnIndicatorHover="true" :showIndicatorsOnItem="inside" :indicatorsPosition="position">
    <template #item="slotProps">
        <img :src="slotProps.item.itemImageSrc" :alt="slotProps.item.alt" style="width: 100%; display: block" />
    </template>
</Galleria>`,
                options: `
<template>
    <div class="card">
        <div class="flex flex-wrap gap-3 mb-5">
            <div v-for="option in positionOptions" :key="option.label" class="flex align-items-center">
                <RadioButton :value="option.value" />
                <label :for="option.label" class="ml-2"> {{ option.label }} </label>
            </div>
        </div>
        <div class="flex align-items-center mb-5">
            <Checkbox v-model="inside" inputId="inside_cbox" :binary="true"></Checkbox>
            <label for="inside_cbox" class="ml-2"> Inside </label>
        </div>
        <Galleria :value="images" :numVisible="5" containerStyle="max-width: 640px" :showThumbnails="false" :showIndicators="true" :changeItemOnIndicatorHover="true" :showIndicatorsOnItem="inside" :indicatorsPosition="position">
            <template #item="slotProps">
                <img :src="slotProps.item.itemImageSrc" :alt="slotProps.item.alt" style="width: 100%; display: block" />
            </template>
        </Galleria>
    </div>
</template>

<script>
import { PhotoService } from '@/service/PhotoService';

export default {
    data() {
        return {
            images: null,
            inside: false,
            position: 'bottom',
            positionOptions: [
                {
                    label: 'Bottom',
                    value: 'bottom'
                },
                {
                    label: 'Top',
                    value: 'top'
                },
                {
                    label: 'Left',
                    value: 'left'
                },
                {
                    label: 'Right',
                    value: 'right'
                }
            ]
        };
    },
    mounted() {
        PhotoService.getImages().then((data) => (this.images = data));
    }
};
<\/script>`,
                composition: `
<template>
    <div class="card">
        <div class="flex flex-wrap gap-3 mb-5">
            <div v-for="option in positionOptions" :key="option.label" class="flex align-items-center">
                <RadioButton :value="option.value" />
                <label :for="option.label" class="ml-2"> {{ option.label }} </label>
            </div>
        </div>
        <div class="flex align-items-center mb-5">
            <Checkbox v-model="inside" inputId="inside_cbox" :binary="true"></Checkbox>
            <label for="inside_cbox" class="ml-2"> Inside </label>
        </div>
        <Galleria :value="images" :numVisible="5" containerStyle="max-width: 640px" :showThumbnails="false"
            :showIndicators="true" :changeItemOnIndicatorHover="true" :showIndicatorsOnItem="inside" :indicatorsPosition="position">
            <template #item="slotProps">
                <img :src="slotProps.item.itemImageSrc" :alt="slotProps.item.alt" style="width: 100%; display: block" />
            </template>
        </Galleria>
    </div>
</template>

<script setup>
import { ref, onMounted } from "vue";
import { PhotoService } from '@/service/PhotoService';

onMounted(() => {
    PhotoService.getImages().then((data) => (images.value = data));
});

const images = ref();
const inside = ref(false);
const position = ref('bottom');
const positionOptions = ref([
    {
        label: 'Bottom',
        value: 'bottom'
    },
    {
        label: 'Top',
        value: 'top'
    },
    {
        label: 'Left',
        value: 'left'
    },
    {
        label: 'Right',
        value: 'right'
    }
]);

<\/script>`,
                data: `
/* PhotoService */
{
    itemImageSrc: 'https://primefaces.org/cdn/primevue/images/galleria/galleria1.jpg',
    thumbnailImageSrc: 'https://primefaces.org/cdn/primevue/images/galleria/galleria1s.jpg',
    alt: 'Description for Image 1',
    title: 'Title 1'
},
...
        `
            }
        };
    },
    mounted() {
        PhotoService.getImages().then((data) => (this.images = data));
    }
};
</script>
