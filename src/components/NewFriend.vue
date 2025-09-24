<template>
    <form @submit.prevent="submitData">
        <div>
            <label>name</label>
            <input type="text" v-model="enteredName" />
        </div>
        <div>
            <label>Phone</label>
            <input type="tel" v-model="enteredPhone" />
        </div>
        <div>
            <label>E-mail</label>
            <input type="email" v-model="enteredEmail" />
        </div>
        <div>
            <button>Add Friend</button>
        </div>
    </form>
</template>

<script>
export default {
    emits: ['add-friend'],
    data() {
        return {
            enteredName: '',
            enteredPhone: '',
            enteredEmail: ''
        };
    },
    methods: {
        submitData(){
            console.log('Submitting:',this.enteredName,this.enteredPhone,this.enteredEmail);
            this.$emit('add-friend',this.enteredName,this.enteredPhone,this.enteredEmail);
        }
        
    }
}
    
</script>