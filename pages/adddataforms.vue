<!-- AdminForm.vue -->

<template>
  <div class="admin-form">
    <form @submit.prevent="addData">
      <!-- Add input fields for each column in your table -->
      <label for="column1">Column 1:</label>
      <input type="text" id="column1" v-model="formData.column1" required />

      <label for="column2">Column 2:</label>
      <input type="text" id="column2" v-model="formData.column2" required />

      <!-- Add more input fields as needed -->

      <button type="submit">Add Data</button>
    </form>
  </div>
</template>

<script>
import { ref } from 'vue';
import { createClient } from '@supabase/supabase-js';

const supabaseUrl = 'https://cuetscutmucqyjvweeae.supabase.co';
const supabaseKey = 'eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJpc3MiOiJzdXBhYmFzZSIsInJlZiI6ImN1ZXRzY3V0bXVjcXlqdndlZWFlIiwicm9sZSI6ImFub24iLCJpYXQiOjE3MDU1MDY4NTEsImV4cCI6MjAyMTA4Mjg1MX0.4r60kuj_F12SAdG5sdqpFY0SeXVqjKcV9l8Hq3iy94U';

const supabase = createClient(supabaseUrl, supabaseKey);

export default {
  data() {
    return {
      formData: {
        column1: '',
        column2: '',
        // Add more properties for other columns
      },
    };
  },
  methods: {
    async addData() {
      try {
        const { data, error } = await supabase
          .from('your_table_name')
          .upsert([{ ...this.formData, user_id: supabase.auth.user()?.id }], { returning: 'representation' });

        if (error) {
          console.error('Error adding data:', error.message);
        } else {
          console.log('Data added successfully:', data);
          // Clear the form after successful submission
          this.formData = {};
        }
      } catch (error) {
        console.error('Error adding data:', error.message);
      }
    },
  },
};
</script>

<style scoped>
/* Your styling goes here */
</style>
