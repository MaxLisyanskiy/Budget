<template>
    <div class="budget-list-wrap">
        <ElCard :header="header">
            <template v-if="isEmpty">
                <div class="list-tem" v-for='(item,prop) in list' :key="prop">
                    <div class="budget-comment">{{item.comment}}</div>
                    <div class="budget-value">{{item.value}}</div>
                    <ElButton type="danger" size="mini">Delete</ElButton>
                </div>
            </template>
            <ElAlert v-else type="info" :title="emptyTitle" :closable="false"/>
        </ElCard>
    </div>
</template>

<script>
export default {
    name: 'BudgetList',
    props: {
        list: {
            type: Object,
            defailt: () => ({})
        }
    },
    data: () => ({
        header: 'Budget List',
        emptyTitle: 'Empty Title'
    }),
    computed: {
        isEmpty() {
            return (Object.keys(this.list).length);
        }
    }
}
</script>

<style scoped>
    .budget-list-wrap {
        max-width: 500px;
        margin: auto;
    }
    .list-tem{
        display: flex;
        justify-content: space-between;
        margin-top: 15px;
    }
</style>