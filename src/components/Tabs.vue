<script setup lang="ts">
    import { ref } from "@vue/reactivity";
    import Tab from "./Tab.vue";

    const tabs = [
        {
            title: "Tab 1",
            content: "Essa é a tab 1 Essa é a tab 1 Essa é a tab 1"
        },
        {
            title: "Tab 2",
            content: "Essa é a tab 2 Essa é a tab 2 Essa é a tab 2 Essa é a tab 2"
        },
        {
            title: "Tab 3",
            content: "Essa é a tab 3 Essa é a tab 3 Essa é a tab 3"
        },
    ];

    const selectedTab = ref(0);
    
    const tabOnClick = (tabIndex: number) => {
        selectedTab.value = tabIndex;
    };

    const isTabSelected = (tabIndex: number) => {
        if (tabIndex === selectedTab.value) {
            return true;
        }

        return false;
    };
</script>


<template>
    <div class="tab-buttons-container">
        <Tab
            v-for="(tabItem, index) in tabs" 
            :key="tabItem.title"
            :title="tabItem.title"
            :selected="isTabSelected(index)"
            :index="index"
            @on-click="tabOnClick"
        />

    </div>

    <div class="tab-content-container">
        <section>
            <p>{{tabs[selectedTab].content}}</p>
        </section>
    </div>
</template>

<style scoped>
    .tab-buttons-container {
        width: 35%;
        margin: 10px;
        display: flex;
        justify-content: space-between;
    }

    .tab-content-container {
        display: flex;
        width: 500px;
        height: 250px;
        border: 1  px ridge rgb(177, 174, 174);
        border-radius: 4px;
        background-color: rgb(250, 250, 250);
    }

    .tab-content-container p {
        color: black;
    }
</style>