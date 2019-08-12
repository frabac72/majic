<template>
    <div>
        {{ activeTab }}
        <roles v-if='activeTab==="AA"'/>
        <epic v-if='activeTab==="BB"'/>
        <Progress v-if='activeTab==="CC"'/>
        <config v-if='activeTab==="DD"'/>
    </div>
</template>


<script>
import roles from './RolesAndPeople'
import epic from './EpicAndIssues'
import Progress from './Progress'
import config from './Config'

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
    }

}
</script>