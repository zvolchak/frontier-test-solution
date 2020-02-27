<template lang="pug">
  #UserData
    section#active-account-column.account-column.grid
      #active-account-container-title.account-container-title
        h3 Active
      .account-container.active-account
        ul.account-data-list
          li
            label Name:
            |  {{LastName}}, {{FirstName}}
          li
            label Email:
            |  {{Email}}
          li
            label Phone Number:
            |  {{phoneNumberFormatted}}
          li
            label Amount Due:
            |  {{amountFormatted}}
          li
            label Due Date:
            |  {{dueDateFormatted}}


</template>

<script>
export default {
  name: 'UserData',
  props: {
    LastName: { type: String },
    FirstName: { type: String },
    Email: { type: String },
    PhoneNumber: { type: String },
    AmountDue: { type: Number },
    DueDate: { type: String },
    Id: { type: Number },
    Status: {type: Number },
  },//props



  computed: {
    phoneNumberFormatted() {
      //TODO: validate phone number format. Clarify requirements on wrong input format.
      //source: https://stackoverflow.com/questions/8760070/how-to-format-a-phone-number-with-jquery
      return this.PhoneNumber.replace(/(\d{3})(\d{3})(\d{4})/, '($1)-$2-$3');
    },//phoneNumberFormatted


    dueDateFormatted() {
      //TODO: validate date format. Clarify requirements on wrong input format.
      let date = new Date(this.DueDate)
      return date.getMonth() + '/' + date.getDay() + '/' + date.getFullYear()
    },//dueDateFormatted


    amountFormatted() {
      let formatter = new Intl.NumberFormat('en-US', {
        style: 'currency',
        currency: 'USD',
      });
      return formatter.format(this.AmountDue)
    },//amountFormatted

  },//computed

}//default
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style lang="scss" scoped>
</style>
