<template>
    <div class="budget-list-wrap">
        <elCard :header="header">
            <template v-if="!isEmpty">
                <div class="list-item" v-for="(item, prop) in list" :key="prop">
                    <span class="budget-comment">{{ item.comment }}</span>
                    <span class="budget-value">{{ item.value }}</span>
                    <ElButton type="danger" size="mini">Delete</ElButton>
                </div>
            </template>
            <ElAlert v-else type="info" :title="emptyList"></ElAlert>
        </elCard>
    </div>
</template>

<script>
export default {
    name: 'BudgetList',
    props: {
        list: {
            type: Object,
            default: () => ({})
        }
    },
    data: () => ({
        header: 'Budget List',
        emptyList: 'Empty List'
    }),
    computed: {
        isEmpty() {
            return !Object.keys(this.list).length
        }
    }
}
</script>

<style lang="stylus" scoped>
.budget-list-wrap 
    width 500px
    margin 0 auto
.list-item
    display flex
    align-items center
    padding 10px 15px
.budget-value
    font-weight bold
    margin-left  auto
    margin-right 20px
</style>