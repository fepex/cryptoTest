<template>
    <div>
        <div class="flex">
            <div v-for="(data, index) in linksStore" :key="index">
                <img class="icons" :src="getImageUrl(data.img)" @click="getLink(data.link)">
            </div>
        </div>
        <div class="iframeDiv"><iframe :src="currentSiteSrc"></iframe></div>

    </div>
</template>

<script>
import siteData from '@/components/dockPanel/dockPanelSite.json'

export default {
    name: 'GetShaCode',
    data() {
        return {
            linksStore: siteData,
            currentSiteSrc: '',
        }
    },
    methods: {
        getImageUrl(img) {
            return require('@/assets/' + img);
        },
        getLink(clicked) {
            this.currentSiteSrc = clicked;
        }
    }
};
</script>

<style lang="css" scoped>
.flex {
    display: flex;
}

.icons {
    height: 30px;
    margin-right: 15px;
}

.icons:hover {
    height: 50px;
}

iframe {
    height: 700px;
    width: 100%;
}
</style>