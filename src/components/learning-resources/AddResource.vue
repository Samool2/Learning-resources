<template>
<base-dialog v-if="inputIsInvalid" title="Invalid input.">
<template #default>
    <p>Every field requires at least a few characters!</p>
</template>
<template #actions>
    <base-button @click="confirmError">OK</base-button>
</template>
</base-dialog>
  <base-card>
    <form @submit.prevent>
        <div class="form-control">
            <label for="title">Title</label>
            <input id="title" name="title" type="text" ref="titleInput">
        </div>
        <div class="form-control">
            <label for="description">Description</label>
            <textarea name="description" id="description" ref="descriptionInput" rows="3"></textarea>
        </div>
        <div class="form-control">
            <label for="link">Link</label>
            <input id="link" name="Link" ref="linkInput" type="url">
        </div>
        <div>
            <base-button type="submit" @click="submitData">Add Resource</base-button>
        </div>
    </form>
  </base-card>
</template>


<script>
import BaseDialog from '../UI/BaseDialog.vue';
export default {
  components: { BaseDialog },

    inject:['addResource'],

    data() {

        return {

                inputIsInvalid: false
        }

    },

    methods: {
        submitData() {
            const enteredTitle = this.$refs.titleInput.value;
            const enteredDescription = this.$refs.descriptionInput.value;
            const enteredLink = this.$refs.linkInput.value;
            if(enteredTitle.trim() != '' || enteredDescription.trim() != '' || enteredLink.trim() != '')
            {
                this.addResource(enteredTitle, enteredDescription, enteredLink)
                this.$refs.titleInput.value = ''
                this.$refs.descriptionInput.value = ''
                this.$refs.linkInput.value = ''

                } else {
                    console.warn('Text required in all fields.')
                    this.inputIsInvalid = true
                }
            

        },
        confirmError() {
            this.inputIsInvalid = false;
        }
        
        
    },
    provide() {
        return {

        }
    }
    

}
</script>


<style scoped>

label {
  font-weight: bold;
  display: block;
  margin-bottom: 0.5rem;
}

input,
textarea {
  display: block;
  width: 100%;
  font: inherit;
  padding: 0.15rem;
  border: 1px solid #ccc;
  border-radius:5px;
  box-shadow:0 2px 8px rgba(0,0,0,0.26);
}

input:focus,
textarea:focus {
  outline: none;
  border-color: #3a0061;
  background-color: #f7ebff;
}

.form-control {
  margin: 1rem 0;
}

</style>