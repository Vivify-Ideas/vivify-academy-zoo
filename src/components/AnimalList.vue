<template>
  <div>
    <h1>Animals</h1>
    <table class="table">
      <thead>
        <tr>
          <th>Species</th>
          <th>Name</th>
          <th>Date of birth</th>
          <th>&nbsp;</th>
        </tr>
      </thead>
      <tbody>
        <tr v-for="(animal, key) in animals" :key="key">
          <td>{{ animal.species }}</td>
          <td>{{ animal.name }}</td>
          <td>{{ animal.dateOfBirth ? animal.dateOfBirth : 'Nepoznat' }}</td>
          <td class="text-right">
            <button class="btn btn-danger btn-sm" @click="remove(animal)">Remove</button>
            <button class="btn btn-default btn-sm" @click="moveToTop(animal)">Move to top</button>
          </td>
        </tr>
      </tbody>
    </table>
  </div>
</template>

<script>
export default {
  name: 'AnimalList',
  data() {
    return {
      animals: [
        {
          species: 'Dog',
          name: 'Ben',
          dateOfBirth: '12-12-2012'
        },
        {
          species: 'Cat',
          name: 'Cloe',
          dateOfBirth: '05-05-2010'
        },
        {
          species: 'Parot',
          name: 'Jargo',
          dateOfBirth: '24-02-2015'
        },
        {
          species: 'Fish',
          name: 'Nemo',
          dateOfBirth: ''
        },
        {
          species: 'Horse',
          name: 'Thunder',
          dateOfBirth: ''
        }
      ]
    };
  },
  methods: {
    remove(animal) {
      const index = this.animals.indexOf(animal);
		  this.animals.splice(index, 1);
    },
    moveToTop(animal) {
      this.remove(animal);
      this.animals.unshift(animal);
    }
  }
};
</script>
