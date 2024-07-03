<template>
    <div>
        <li>
            <h2>{{ name }} {{friendIsFav == 1 ? '(Favourite)' : ''}}</h2>
            <button @click="toggleFAv">Toggle Favourite</button>
            <button @click="toggleDetails">{{ detailsAreVisible ? 'Hide' : 'Show' }} Details</button>
            <ul v-if="detailsAreVisible">
                <li>
                    <strong>Phone:</strong>
                    {{ phone }}
                </li>
                <li>
                    <strong>Email:</strong>
                    {{ email }}
                </li>
            </ul>
        </li>
    </div>
</template>

<script>
export default {
    props: ["name", "email", "id", "phone", "isFavourite"],
    data() {
        return {
            detailsAreVisible: false,
            friendIsFav : this.isFavourite
        };
    },
    methods: {
        toggleDetails() {
            this.detailsAreVisible = !this.detailsAreVisible;
        },
        toggleFAv(){
            if(this.friendIsFav == '1'){
                this.friendIsFav = '0'
            }
            else{
                this.friendIsFav = '1'
            }
        }
    }
};
</script>