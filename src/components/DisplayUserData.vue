<template lang="pug">
  #DisplayUserData
    section.grid
    header.grid
      .title-container
        h1 Coding Test
    main#home-content.content.grid
      .content-title-container
        h2 Accounts
      section#account-grid.grid
        template(v-for="item in userData")
          UserData(v-if="item.PaymentDueDate || (!item.PaymentDueDate && item.AccountStatusId > 0)"
            :FirstName="item.FirstName"
            :LastName="item.LastName"
            :Email="item.Email"
            :PhoneNumber="item.PhoneNumber"
            :AmountDue="item.AmountDue"
            :DueDate="item.PaymentDueDate"
          )
    footer.grid
      p.copy {{ new Date().getFullYear()}}

</template>

<script>
import UserData from '@/components/UserData'
import axios from 'axios'


export default {
  name: 'DisplayUserData',

  components: {
    UserData
  },//cmp

  props: {
  },//props


  data() {
    return {
      userData: {},
    }
  },//data

  created() {
    this.getUserData()
  },


  methods: {
    getUserData() {
      //TODO: move url to a vue.config.js to use defaults or read from env
      let url = 'https://frontiercodingtests.azurewebsites.net/api/accounts/getall'
      // this.userData = [
      //   {"Id":1,"FirstName":"Emma","LastName":"Smith","Email":"emma.smith@email.com","PhoneNumber":"5555559483","AmountDue":84.22,"PaymentDueDate":"2020-03-04T00:00:00+00:00","AccountStatusId":0},
      //   {"Id":1,"FirstName":"AAAA","LastName":"Smith","Email":"emma.smith@email.com","PhoneNumber":"5555559483","AmountDue":84.22,"PaymentDueDate":null,"AccountStatusId":0},
      //   {"Id":2,"FirstName":"Noah","LastName":"Johnson","Email":"noah.johnson@email.com","PhoneNumber":"5555557383","AmountDue":123.76,"PaymentDueDate":"2020-03-19T00:00:00+00:00","AccountStatusId":0},{"Id":3,"FirstName":"Abigail","LastName":"Williams","Email":"abigail.williams@email.com","PhoneNumber":"5555553928","AmountDue":42.45,"PaymentDueDate":"2020-03-16T00:00:00+00:00","AccountStatusId":0},{"Id":4,"FirstName":"Mason","LastName":"Brown","Email":"mason.brown@email.com","PhoneNumber":"5555550394","AmountDue":0.0,"PaymentDueDate":null,"AccountStatusId":1},{"Id":5,"FirstName":"Emily","LastName":"Miller","Email":"emily.miller@email.com","PhoneNumber":"5555556958","AmountDue":355.67,"PaymentDueDate":"2020-02-12T00:00:00+00:00","AccountStatusId":2},{"Id":6,"FirstName":"Michael","LastName":"Davis","Email":"michael.davis@email.com","PhoneNumber":"5555550394","AmountDue":0.0,"PaymentDueDate":null,"AccountStatusId":1},{"Id":7,"FirstName":"Joshua","LastName":"Garcia","Email":"joshua.garcia@email.com","PhoneNumber":"5555559283","AmountDue":98.35,"PaymentDueDate":"2020-02-20T00:00:00+00:00","AccountStatusId":2}]
      axios.get(url)
        .then(response => {
          this.userData = response.data
          //TODO: Check with the the requirements on user validation.

          //FIXME: should be a customizable way of passing different sorting functions
          this.userData.sort(function(a, b) {
            return a.AccountStatusId > b.AccountStatusId;
          })
        })
      .catch(e => {
        console.log(e)
      })

      //TODO: add some sort of data caching support; Explore the possability to
      //use Store to save data and pass around different views.

      //TODO: Explore any Security concerns regarding this user's data storage.
    },//getUserData

  },//methods

}//default
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style lang="scss" scoped>
</style>
