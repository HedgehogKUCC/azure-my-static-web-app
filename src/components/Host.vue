<template>
  <section>
    <div class="nav-bar"></div>
    <h1>Relecloud Galaxy Tours</h1>
    <br>

    <h2>Component: UserDisplay</h2>
    <user-display :user="user"></user-display>

    <br>

    <h2>Component: UserDialog</h2>
    <user-dialog @dialog-updated="handleDialogUpdated"></user-dialog>

    <br>
    <div>
        <h2>{{ cruise.name }}</h2>
        <div>{{ cruise.description }}</div>
        <hr />

        <div class="row">
            <div>
                <!-- TODO: Add booking-form -->
                <booking-form :cabins="cruise.cabins" @booking-created="handleBookingCreated"></booking-form>
            </div>
            <div>
                <!-- TODO: Add booking-list -->
                <booking-list :bookings="bookings"></booking-list>
            </div>
        </div>
    </div>
  </section>
</template>

<script>
  import UserDisplay from './UserDisplay.vue';
  import UserDialog from './UserDialog.vue';
  import BookingList from './BookingList.vue';
  import BookingForm from './BookingForm.vue';

  export default {
    name: 'Host',
    components: {
      UserDisplay,
      UserDialog,
      BookingForm,
      BookingList,
      // TODO: Add next component
    },
    data() {
      return {
        user: {
          name: 'KUCC',
          age: 31,
        },
        cruise: {
          name: 'Cruise to the moon',
          description: 'Cruise to the moon in our luxurious shuttle. Watch the astronauts working outside the International Space Station.',
          cabins: [
            { name: 'Coach', price: 125000 },
            { name: 'Business', price: 275000 },
            { name: 'First', price: 430000 },
          ]
        },
        bookings: []
      }
    },
    // TODO: Add methods
    methods: {
      handleDialogUpdated(status) {
        if (status) {
          alert('It worked!!');
        } else {
          alert('Something went wrong');
        }
      },
      handleBookingCreated(index) {
        const cabin = this.cruise.cabins[index];
        const booking = {
            cabin: cabin.name,
            price: cabin.price
        }
        this.bookings.push(booking);
      }
    }
  }
</script>

<style scoped>
body {
    background-color: #f2f2f2;
    margin: 0, 5%;
    font-family: tahoma;
}

.row {
    display: grid;
    grid-template-columns: 1fr 1fr;
    vertical-align: middle;
    margin: 2em;
}

.button {
    background-color: #39495c;
    border-radius: 5px;
    color: white;
    text-align: center;
}

.nav-bar {
    background: linear-gradient(-50deg, #010801, #0d0d60);
    height: 60px;
    margin-bottom: 25px;
}
</style>