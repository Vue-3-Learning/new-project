<template>
    <div>
        <li>
            <h2>{{ name }} {{ isFavourite ? '(Favourite)' : '' }}</h2>
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
    props: {
        isFavourite: {
            type: Boolean,
            default: false
        },
        name: {
            required: true
        }, 
        id: {
            required: true
        },
        email: {
            required: true
        }, 
        phone: {
            required: true
        }

    },
    data() {
        return {
            detailsAreVisible: false,
            friendIsFav: this.isFavourite
        };
    },
    methods: {
        toggleDetails() {
            this.detailsAreVisible = !this.detailsAreVisible;
        },
        toggleFAv() {
            this.$emit('toggle-friend', this.id)
        }
    }
};
</script>