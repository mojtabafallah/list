<script>
export default {
    data() {
        return {
            color: 'red',
            fs: 20,
            users: [
                {
                    id: 1,
                    name: 'ali',
                    family: 'alavi',
                    age: 30,
                    job: 'developer'
                },
                {
                    id: 2,
                    name: 'hasan',
                    family: 'alavi',
                    age: 35,
                    job: 'developer2'
                },
                {
                    id: 3,
                    name: 'reza',
                    family: 'rezaee',
                    age: 36,
                    job: 'developer3'
                },
                {
                    id: 1,
                    name: 'ali',
                    family: 'alavi',
                    age: 30,
                    job: 'developer4'
                }
            ],
            user_data: {

            },
            count: 0,
            ageNormal : 0,
            ageFlag : 3,
            showMessage: false,
            color: "",
            color2: "#fff",
            family: "test"
        }
    },
    computed: {
        checkAge() {
            return this.users.filter(item => item.age > 32);
        }
    }, watch:{
       ageNormal(newValue,oldValue){
         this.showMessage = newValue <= this.ageFlag;
       }
    },
    methods:{
        addCount(){ this.count++ },
        plusCount(value){
            if(value) this.ageNormal ++; else this.ageNormal--;
        }
    },
    beforeCreate(){
        alert('brefore create');
    },
    created(){
        alert(' created');
    },beforeMount(){
        alert(' beformonte');
    },mounted(){
        alert(' mounted');
    },beforeUpdate(){
        alert(' beforeUpdate');
    },updated(){
        alert(' updated');
    },beforeDestroy(){
        alert('befor destroy');
    },destroyed(){
        alert('destoyrd');
    }
    
}
</script>

<template>
    <p :style="{ color: color, fontSize: fs + 'px' }"> this is a text </p>
    <table border="1" cellpadding="0" cellspacing="0">
        <thead>
            <th>row</th>
            <th>name family</th>
            <th>age</th>
            <th>job</th>
        </thead>
        <tbody>
            <tr v-for="(user, index) in users" :key="user.id">
                <td>{{ index + 1 }}</td>
                <td>{{ user.name + user.family }}</td>
                <td>{{ user.age }}</td>
                <td>{{ user.job }}</td>
            </tr>
        </tbody>
    </table>
    <ul>

        <li v-for="user in checkAge">{{ user.name + '-' + user.age }}</li>

    </ul>
    <h2>Count:{{ count }}</h2>
    <button @click="addCount()">test</button>

    <hr>
    <h2>your age: {{ ageNormal }}</h2>
    <p v-if="showMessage">you are baby</p>
    <p v-else> you  are man</p>
    <button @click="plusCount(true)">+</button>
    <button @click="plusCount(false)">-</button>
    <hr>

    <hr>
    <select name="favColor" id="" v-model="color">
        <option value="">Select Color</option>
        <option value="blue">Blue</option>
        <option value="red">Red</option>
        <option value="green">Green</option>
        <option value="orange">orange</option>
    </select>
    <p :style="{backgroundColor: color}">{{ color }}</p>
    <hr>
    <input type="color" v-model="color2">
    <p :style="{backgroundColor: color2}">test</p>
    <hr>
    <input type="text" v-model.lazy="family">{{ family }}
    <hr>
    <input type="text" ref="desRef">
    <button @click=""></button>
</template>
<style>

</style>