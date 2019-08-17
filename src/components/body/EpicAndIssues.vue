<template>
    <div>
        <p>This is the Epic and Issues page</p>
        <p>Search for issues to clone</p>
        <p>by label <input type="text" v-model="label"/> <button @click="searchByLabel">Go</button></p>
        <p>by EPIC <input type="text" /> <button @click="searchByEpic">Go</button></p>
        <ul>
            <li v-for="item in items" :key="item"></li>
        </ul>
        <div>AA {{ outcome }} AA</div>
        <div>BB {{ datas }} BB</div>
    </div>
</template>

<script>
// const jira_search_base_url = 'https://confluence.alfahub.net/questions/54399185/retriableexectutor---dialling-back-the-retry-logic'
const jira_search_base_url = 'https://jira.dev.alfahub.io/rest/api/2/search?jql='

export default {
    methods : {
        searchByLabel() {
            alert('a');
            // var resultArray = []
            var url = jira_search_base_url + 'labels%20=%20SOW18';
            alert(url)
            this.$http.get(url)      
                .then(
                    response => {
                        this.outcome='success';
                        // eslint-disable-next-line
                        console.log(response);
                    },
                    err => {
                       this.outcome = 'error';
                       // eslint-disable-next-line
                       console.log(err);
                    })
                .catch((e) => {
                    this.outcome= "Caught"
                    // eslint-disable-next-line
                    console.log(e);
                });
            alert('b');
        },
        searchByEpic() {

        }
    },
    data : function(){
        return {
            label: '',
            items : [],
            outcome : '',
            datas : ''
        }
    }


}
</script>