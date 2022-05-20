<script setup lang="ts">
    interface TabProps {
        title: string;
        selected: boolean;
        index: number;
    }

    interface TabEvents {
        onClick: (index: number) => void;
    }

    defineProps<TabProps>();
    defineEmits<TabEvents>();

    
</script>

<template>
    <button
        type="button"
        :class="{selected: selected}"
        :title="$props.title"
        @click="$emit('onClick', index)"
    >
        {{ title }}
    </button>
</template>
