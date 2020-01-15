<template>
  <div>
    <input type="number" @change="push" v-model.number="form.valueFirst" placeholder="введите первое значение">
    <input type="number" @change="push" v-model.number="form.valueSecond" placeholder="введите второе значение">
  </div>
</template>

<script>
export default {
    model:{
        event:'change'
    },
    data(){
        return{
            form:{
                valueFirst:0,
                valueSecond:0
            }
        }
    },
    methods: {
        push(){
            this.$emit('change', this.form)
        }
    },
}
</script>