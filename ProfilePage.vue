<template>
  <div class="profile-page">
    <div class="profile-header">
      <!-- Profile Photo -->
      <img :src="profile.photo" alt="Profile Photo" class="profile-photo" />
      <h1>{{ profile.name }}</h1>
      <p class="bio">{{ profile.bio }}</p>
    </div>
  
    <div class="social-links">
      <a v-for="(link, platform) in profile.socialMediaLinks" 
         :key="platform" 
         :href="link"
         :title="platform"
         target="_blank" 
         class="social-link">
        <img :src="getIcon(platform)" :alt="platform" />
      </a>
    </div>
  
    <!-- Navigation Buttons -->
    <div class="navigation-buttons">
      <button @click="navigateTo('creative')" class="nav-btn">Creative</button>
      <button @click="navigateTo('contact')" class="nav-btn">Contact</button>
      <button @click="navigateTo('showcase')" class="nav-btn">Showcase</button>
      <button @click="logout" class="nav-btn logout-btn">Logout</button>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      profile: {
        name: 'Joice Ann Eisley M. Viernes',
        photo: require('/public/me.jpg'), // Ensure this path is correct
        bio: '"Joice Ann Eisley Viernes is a chess player from the Philippines, recognized for participating in various youth chess tournaments. She has competed in events such as the 13-and-below categories in tournaments like the "En Passant Independence Day Rapid Chess Tournament" and the "SM San Mateo Youth Rapid Chess Tournament." Her performance in these competitions has earned her a rating of 1752 at different points in her career. For further details, you can find more information on her player profiles on sites like Chess.com and Pinoy Chess Players."',
        socialMediaLinks: {
          Facebook: 'https://www.facebook.com/kittyrawrme',
          GitHub: 'https://github.com/icesmoker',
        },
      },
    };
  },
  methods: {
    getIcon(platform) {
      switch (platform) {
        case 'Facebook':
          return require('/public/fb.png');
        case 'GitHub':
          return 'https://upload.wikimedia.org/wikipedia/commons/9/91/Octicons-mark-github.svg';
        default:
          return '';
      }
    },
    navigateTo(page) {
      this.$router.push(`/portfolio/${page}`);
    },
    logout() {
      // Perform logout logic here (e.g., clear tokens, user session)
      this.$router.push('/login'); // Redirect to login page
    },
  },
};
</script>

<style scoped>
/* Overall Page Layout */
.profile-page {
  background: url('/public/bg2.gif'); /* Add your GIF path here */
  background-size: cover;  /* Make sure the background covers the entire page */
  text-align: center;
  max-width: 600px;
  margin: 50px auto;
  padding: 30px;
  border-radius: 8px;
  box-shadow: 0 4px 8px rgba(0, 0, 0, 0.1);
  font-family: 'Arial', sans-serif;
}

/* Profile Header */
.profile-header {
  margin-bottom: 20px;
}

.profile-photo {
  width: 150px;
  height: 150px;
  border-radius: 50%;
  border: 4px solid #0c0c0c; 
  box-shadow: 0 0 15px rgba(0, 0, 0, 0.1);
  transition: transform 0.3s ease-in-out;
}

.profile-photo:hover {
  transform: scale(1.1);
}

h1 {
  color: #fff; /* Adjust text color to stand out against the GIF background */
  font-size: 2.2rem;
  font-weight: 600;
  margin-top: 15px;
}

.bio {
  font-style: italic;
  color: #ddd; /* Light color for bio text */
  font-size: 1rem;
  max-width: 500px;
  margin: 20px auto;
}

/* Social Media Icons */
.social-links {
  display: flex;
  justify-content: center;
  gap: 20px;
  margin: 20px 0;
}

.social-link img {
  width: 40px;
  height: 40px;
  transition: transform 0.3s ease;
}

.social-link img:hover {
  transform: scale(1.2);
}

/* Navigation Buttons */
.navigation-buttons {
  margin-top: 30px;
  display: flex;
  justify-content: center;
  gap: 15px;
}

.nav-btn {
  background-color: #2b90d9; 
  color: white;
  padding: 12px 25px;
  border: none;
  border-radius: 30px;
  cursor: pointer;
  font-size: 16px;
  transition: background-color 0.3s ease, transform 0.3s ease;
  box-shadow: 0 2px 4px rgba(0, 0, 0, 0.1);
}

.nav-btn:hover {
  background-color: #277db2;
  transform: translateY(-3px);
}

.nav-btn:active {
  transform: translateY(1px);
}

/* Logout Button Styles */
.logout-btn {
  background-color: #d9534f;
}

.logout-btn:hover {
  background-color: #c9302c;
}

/* Mobile Responsiveness */
@media (max-width: 768px) {
  .profile-page {
    padding: 15px;
  }

  .social-links {
    gap: 10px;
  }

  .nav-btn {
    padding: 10px 20px;
    font-size: 14px;
  }
}
</style>
