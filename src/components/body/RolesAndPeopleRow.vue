<template>
    <span>
        <table>
            <tr>
                <td colspan="3">
                    CC {{ value }} CC
                </td>
            </tr>
            <!----><tr>
                <td>
                    <input type="text" v-bind:value='value["therole"]'/>
                </td>
                <td>
                    <select v-model="selected" @change="nameSelected">
                        <option v-for="person in persons" :key='person'>{{  person }}</option>
                    </select>
                </td> 
                <td>
                    <input v-if="isOtherSelected" type="text" v-model='value["thename"]' @input="nameChanged"/>
                </td>
            </tr>
        </table>
    </span>
</template>

<script>

const other = 'other...';

export default {
    props : {
        persons : Array,
        value : Object
    },
    computed : {
        isOtherSelected() {
            return this.selected === other;
        }
    },
    data : function() {
        return {
            selected : this.value["thename"]
        }
    },
    methods : {
        nameChanged() {
            this.$emit('input', this.value);
            this.$emit('refresh-persons');
        },
        nameSelected(){
            if (this.selected != other) {
                alert(this.selected)
                this.value.thename = this.selected;
                this.$emit('input', this.value);
            }
        }
    }

}
//alert (this.value);
</script>