<template>
  <div class="creative-page">
    <!-- Back Button -->
    <button @click="goBack" class="back-btn">Back to Profile</button>

    <h1 class="title">My Hobbies</h1>
    <div class="hobby-list">
      <div class="hobby-card" v-for="hobby in hobbies" :key="hobby.id">
        <img :src="hobby.photo" :alt="hobby.name" class="hobby-image" />
        <h2 class="hobby-name">{{ hobby.name }}</h2>
        <p class="hobby-description">{{ hobby.description }}</p>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: 'CreativePage',
  data() {
    return {
      hobbies: [
        { id: 1, name: 'Chess', photo: require('/public/unnamed.png'), description: 'Acquired the title of known female chess player from the Philippines. Competed in rated and non-rated tournaments.' },
        { id: 2, name: 'Online Games', photo: require('/public/ml.png'), description: 'Playing online games when free. Flex role but mostly roamer.' },
        { id: 3, name: 'Travelling', photo: require('/public/intra.png'), description: 'Loves to go to historical landmarks.' },
        { id: 4, name: 'Nature Lover', photo: require('/public/ol.png'), description: 'Loves to go overlooking, beach, etc.' },
        { id: 5, name: 'Sing', photo: require('/public/sing.png'), description: 'Former choir member at Antipolo Choir Group.' },
        { id: 6, name: 'Dance', photo: require('/public/dance.png'), description: 'Competed in dance competitions.' },
        { id: 7, name: 'Bike', photo: require('/public/bike.png'), description: 'Loves to ride long distance or short distance.' },
        { id: 8, name: 'Draw', photo: require('/public/draw.png'), description: 'Loves to draw as a hobby.' },
        { id: 9, name: 'Read', photo: require('/public/book.jpg'), description: 'Loves to read books and manga.' },
      ],
    };
  },
  methods: {
    goBack() {
      this.$router.push('/portfolio/profile'); // Navigate back to the profile page
    },
  },
};
</script>

<style scoped>
/* Full-Screen Layout */
.creative-page {
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: flex-start;
  height: 100vh;
  width: 100vw;
  text-align: center;
  padding: 20px;
  font-family: 'Arial', sans-serif;
  background-color: #10cdf7;
  box-sizing: border-box;
  overflow: auto; /* Allows scrolling */
}

/* Title Styling */
.title {
  font-size: 2.5rem;
  margin-bottom: 30px;
  color: #333;
  font-weight: 600;
  width: 100%;
  text-align: center;
}

/* Hobby List Styling */
.hobby-list {
  display: flex;
  flex-wrap: wrap;
  justify-content: center;
  gap: 20px;
  width: 100%;
  max-width: 1200px;
}

.hobby-card {
  flex: 1 1 calc(33.333% - 40px); /* Responsive card layout */
  max-width: 300px;
  min-width: 250px;
  border: 1px solid #ddd;
  border-radius: 8px;
  padding: 15px;
  box-shadow: 0 4px 6px rgba(0, 0, 0, 0.1);
  transition: transform 0.3s ease;
  background-color: white;
}

.hobby-card:hover {
  transform: scale(1.05);
}

.hobby-image {
  width: 100%;
  height: 200px;
  object-fit: cover;
  border-radius: 8px;
}

.hobby-name {
  font-size: 1.5rem;
  margin: 15px 0;
  color: #555;
  font-weight: 600;
}

.hobby-description {
  font-size: 1rem;
  color: #666;
}

/* Fixed Back Button Styling */
.back-btn {
  position: fixed;
  top: 20px;
  left: 20px;
  background-color: #f52424; /* GitHub Blue */
  color: white;
  padding: 10px 20px;
  border: none;
  border-radius: 5px;
  cursor: pointer;
  font-size: 16px;
  z-index: 1000; /* Ensure it stays on top of other elements */
  transition: background-color 0.3s ease;
}

.back-btn:hover {
  background-color: #277db2;
}

/* Mobile Responsiveness */
@media (max-width: 768px) {
  .title {
    font-size: 2rem;
  }

  .hobby-card {
    flex: 1 1 100%;
    max-width: 100%;
    min-width: 100%;
  }
}
</style>
