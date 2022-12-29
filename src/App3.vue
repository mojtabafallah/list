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
            showMessage: false
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
</template>
<style>

</style>