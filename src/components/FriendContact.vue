<template>
<li>
    <h2>{{ name }} {{ isFavorite? '(Favorite)':'' }}</h2>
    <button @click="toggleFavotite">{{ isFavorite?'Unfavorite':'Favorite' }}</button>
    <button @click="toggleDetails">Show details</button>
    <ul v-if="detailsIsVisible">
        <li><strong>Phone:{{ phoneNumber }}</strong></li>
        <li><strong>Email:{{ emailAddress }}</strong></li>
    </ul>
</li>
</template>
<script>   
export default{
    props:[
        'id',
        'name',
        'phoneNumber',
        'emailAddress',
        'isFavorite'
    ],
data(){
    return{
        detailsIsVisible:false,
        friend:{
            id:'manuel',
            name:'Manuel',
            phone:'123456',
            email:'aaaa@aaa.com'
        },
        myFavorite:this.isFavorite
    };   
},
methods:{
    toggleDetails(){
        this.detailsIsVisible = !this.detailsIsVisible;
    },
    toggleFavotite(){
        //this.myFavorite=!this.myFavorite;
        this.$emit('toggle-favorite',this.id);
    }
}

}
</script>