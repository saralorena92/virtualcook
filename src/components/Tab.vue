<template>
    <div :class="{
        flex: variant === 'horizontal',
    }">
        <ul :class="{
            tabs: variant === 'vertical',
        }">
            <li @click="currentTab = index" :class="{ active: currentTab === index }" v-for="(tab, index) in tabList"
                :key="index">
                <label :for="`${_uid}${index}`" v-text="tab" />
                <input :id="`${_uid}${index}`" type="radio" :name="`${_uid}-tab`" :value="index + 1"
                    v-model="activeTab" />
            </li>
        </ul>

        <template v-for="(tab, index) in tabList">
            <div :key="index" v-if="index + 1 === activeTab">
                <slot :name="`tabPanel-${index + 1}`" />
            </div>
        </template>
    </div>
</template>

<script>
export default {
    props: {
        tabList: {
            type: Array,
            required: true,
        },
        variant: {
            type: String,
            required: false,
            default: () => "vertical",
            validator: (value) => ["horizontal", "vertical"].includes(value),
        },
    },
    data() {
        return {
            activeTab: 1,
        };
    },
};
</script>

<style>
.tabs {
    list-style-type: none;
    padding: 36px 0;
    display: flex;
    align-items: stretch;
    overflow-x: auto;

}

.tabs li {
    position: relative;
    font-size: 1.125rem;
    padding-right: 12px;
    opacity: .5;
}

.tabs li label::after {
    content: "";
    position: absolute;
    bottom: -10px;
    right: 0;
    left: 0;
    margin: auto;
    width: 0;
    height: 6px;
    background-color: var(--vt-c-primary);
    border-radius: 5px;
}

.tabs li input {
    position: absolute;
    z-index: 9;
    opacity: 0;
    width: 100%;
    inset: 0;
    cursor: pointer;
}

.tabs li.active label {
    font-weight: 700;
}

.tabs li.active {
    opacity: 1;
}

.tabs li.active label::after {
    width: 30px;
}
</style>