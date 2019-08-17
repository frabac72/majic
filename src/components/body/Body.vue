<template>
    <div>
        <roles v-if='activeTab==="AA"' v-bind:roles="roles" v-bind:persons="persons" @refresh-persons="updateListOfPersons"/>
        <epic v-if='activeTab==="BB"'/>
        <Progress v-if='activeTab==="CC"'/>
        <config v-if='activeTab==="DD"'/>
        <!-- <div>
            {{ persons }}
        </div> -->
    </div>
</template>


<script>
import roles from './RolesAndPeople'
import epic from './EpicAndIssues'
import Progress from './Progress'
import config from './Config'

const other = 'other...'

export default {
    
    name : 'body',
    props : {
        activeTab : String
    },
    components : {
        roles,
        epic,
        Progress,
        config
    },
    data : function() {
        return {
            roles : [
                {
                    therole : 'Release Manager',
                    thename : ''
                }, 
                {
                    therole : 'UAT Manager',
                    thename : ''
                }, 
                {
                    therole : 'Tech Lead',
                    thename : ''
                }, 
                {
                    therole : 'PVT Lead',
                    thename : ''
                }
            ],
            persons : [other]
        }
    },
    methods : {
        updateListOfPersons () {
            var associatedPersons = [];
            for (let index = 0; index < this.roles.length; index++) {
                const personName = this.roles[index].thename;
                if (!associatedPersons.includes(personName) && personName) {
                    associatedPersons.push(personName);
                }
            }
            associatedPersons.push(other);
            // alert(associatedPersons);
            this.persons = associatedPersons
        }
    }
}
</script>