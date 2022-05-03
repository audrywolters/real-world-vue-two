<template>
    <h1>Events for Good</h1>
    <div class="events">
        <EventCard v-for="event in events" :key="event.id" :event="event" />
    </div>
</template>

<script>
    // @ is an alias to /src
    // import axios from 'axios'
    import EventCard from '@/components/EventCard.vue'
    import EventService from '@/services/EventService.js'

    export default {
        name: 'EventList',
        components: {
            EventCard
        },
        data() {
            return {
                events: null
            }
        },
        created() {
            EventService.getEvents()
                .then(response => {
                    this.events = response.data
                })
                .catch(error => {
                    console.log(error)
                })
        }
        // testing axios w/ rob's help
        //mounted() {

        //    console.log('in mounted call');

        //    axios.get(`https://random-data-api.com/api/users/random_user`)
        //        .then(result => {
        //            console.log('get successful, result.data:', result.data);
        //        })
        //        .catch(err => {
        //            console.log('error on get', err);
        //        })
        //},
    }
</script>

<style scoped>
    .events {
        display: flex;
        flex-direction: column;
        align-items: center;
    }
</style>