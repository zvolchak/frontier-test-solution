<template lang="pug">
  #UserData
    section.grid
    header.grid
      .title-container
        h1 Coding Test
    main#home-content.content.grid
      .content-title-container
        h2 Accounts
      section#account-grid.grid
        section#active-account-column.account-column.grid
          #active-account-container-title.account-container-title
            h3 Active
          .account-container.active-account
            ul.account-data-list
              li
                label Name:
                | {{LastName}}, {{FirstName}}
              li
                label Email:
                | {{Email}}
              li
                label Phone Number:
                | {{PhoneNumber}}
              li
                label Amount Due:
                | {{AmountDue}}
              li
                label Due Date:
                | {{DueDate}}
        section#overdue-account-column.account-column.grid
          #overdue-account-container-title.account-container-title
            h3 Overdue
          .account-container.overdue-account
            ul.account-data-list
              li
                label Name:
                | {{LastName}}, {{FirstName}}
              li
                label Email:
                | {{Email}}
              li
                label Phone Number:
                | {{PhoneNumber}}
              li
                label Amount Due:
                | {{AmountDue}}
              li
                label Due Date:
                | {{DueDate}}
        #inactive-account-column.account-column.grid
          #inactive-account-container-title.account-container-title
            h3 Inactive
          .account-container.inactive-account
            ul.account-data-list
              li
                label Name:
                | {{LastName}}, {{FirstName}}
              li
                label Email:
                | {{Email}}
              li
                label Phone Number:
                | {{PhoneNumber}}
              li
                label Amount Due:
                | {{AmountDue}}
              li
                label Due Date:
                | {{DueDate}}
    //- footer.grid
    //-   p.copy
    //-     | &copy;
    //-     script.
    //-       document.write(new Date().getFullYear())

</template>

<script>
export default {
  name: 'UserData',
  props: {
    LastName: {
      type: String
    },
    
    FirstName: {
      type: String
    },

    Email: {
      type: String
    },

    PhoneNumber: {
      type: String,
    },

    AmountDue: {
      type: String,
    },

    DueDate: {
      type: String,
    },
  },//props

}//default
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style lang="scss" scoped>
</style>
