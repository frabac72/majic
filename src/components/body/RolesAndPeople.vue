<template>
    <div>
        This is the Roles and People page
        <div v-for='(role, index) in roles' :key='role'>
            <RolesAndPeopleRow  v-model="roles[index]" v-bind:persons="persons" @refresh-persons="$emit('refresh-persons')"/>
            <!--<div>AA {{ index }} AA</div>
            <div>BB {{ roles[index] }} BB</div>-->
        </div>
        <button @click="addOneMore">Add</button>
         <!--<<div v-for="role in roles" :key="role">
            {{ role.therole }} {{ role.name }}
        </div>-->
    </div>
</template>

<script>
import RolesAndPeopleRow from './RolesAndPeopleRow' 

// const other = 'other...'

export default {
    components : {
        RolesAndPeopleRow
    },
    computed : {

    },
    props : {
        roles : Array,
        persons : Array
    },
    methods : {
        addOneMore() {
            //alert();
            this.roles.push({});
        },

    }
}
</script>