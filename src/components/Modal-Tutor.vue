<template>
  <transition name="modal-fade">
    <div class="modal-backdrop">
      <div class="modal">
        <header class="modal-header">
          <slot name="header">
            Set up tutor profile
          </slot>
          <!-- <button
            type="button"
            class="btn-close"
            @click="close"
            
          >
            x
          </button> -->
        </header>

        <!-- <section class="upload-image">
          <slot>
            <form action="/action_page.php">
            <label for="img">Select image:</label>
            <input type="file" id="img" name="img" accept="image/*">
            <input type="submit">
          </form>
          </slot>
        </section> -->

        <section class="modal-body">
          <slot name ="form">
            <form>
              <!-- <div id="profile">
                <img src="@/assets/img/profile.png" alt="profile image" width="100" height="100">
              </div> -->
              <div id="name">
                <label for="name">Name</label><br>
                <input type="text" id="name" name="name" placeholder="Name"><br>
              </div>
              <div id="gender">
                <label for="gender">Gender</label><br>
                <select id="gender" name="gender">
                  <option value="gender">Select a gender</option>
                  <option value="male">Male</option>
                  <option value="female">Female</option>
                </select>
              </div>
              <br>
              <div id="qualification">
                <label for="qualification">Highest qualification</label><br>
                <select id="qualification" name="qualification">
                  <option value="qualification">Highest qualification</option>
                  <option value="secondary">Secondary</option>
                  <option value="post-secondary">Post-Secondary</option>
                  <option value="secondary">Diploma/Professional Qualification</option>
                  <option value="post-secondary">University</option>
                </select>
              </div>
              <div id="subjects">
                <label for="subjects">Subjects teaching</label><br>
                <form action="/action_page.php">
                  <input type="checkbox" id="english" name="english" value="english">
                  <label for="english"> English</label><br>
                  <input type="checkbox" id="math" name="math" value="math">
                  <label for="math"> Mathematics</label><br>
                  <input type="checkbox" id="science" name="science" value="science">
                  <label for="science"> Science</label><br><br>
                </form>
              </div>
              <br>
              <div id="levels">
                <label for="levels">Levels taught</label><br>
                <form action="/action_page.php">
                  <input type="checkbox" id="primary" name="primary" value="primary">
                  <label for="primary"> Primary</label><br>
                  <input type="checkbox" id="secondary" name="secondary" value="secondary">
                  <label for="secondary"> Secondary</label><br>
                  <input type="checkbox" id="jc" name="jc" value="jc">
                  <label for="jc"> Junior College</label><br><br>
                </form>
              </div>
              <div id="location">
                <label for="location">Location</label><br>
                <input type="text" id="location" name="location" placeholder="Location"><br>
              </div>
              <br>
              <div id="contact">
                <label for="contact">Contact</label><br>
                <input type="text" id="contact" name="contact" placeholder="Contact"><br>
              </div>
              <div id="tele">
                <label for="tele">Telegram</label><br>
                <input type="text" id="tele" name="tele" placeholder="Telegram"><br>
              </div>
            </form>
          </slot>
        </section>

        <!-- <section class="detail-form">
          <slot name ="form">
            <form>
              <label for="fname">First name:</label><br>
              <input type="text" id="fname" name="fname"><br>
              <label for="lname">Last name:</label><br>
              <input type="text" id="lname" name="lname">
            </form>
          </slot>
        </section> -->

        <footer class="modal-footer">
          <!-- <slot name="footer">
            This is the default footer!
          </slot> -->
          <button
            type="button"
            class="btn-orange"
            @click="close"
          >
            Create Profile
          </button>
        </footer>
      </div>
      <div class="close" @click="$emit('close')">
        <img class="close-img" src="@/assets/close-icon.png" alt="" />
      </div>
    </div>
  </transition>
</template>

<script>
  export default {
    name: 'ModalTutor',
    methods: {
      close() {
        this.$emit('close');
      },
    },
  };
</script>

<style>
  .modal-backdrop {
    position: fixed;
    top: 0;
    bottom: 0;
    left: 0;
    right: 0;
    background-color: rgba(0, 0, 0, 0.3);
    display: flex;
    justify-content: center;
    align-items: center;
  }

  .modal {
    background: #f6f5f6;
    box-shadow: 2px 2px 20px 1px;
    overflow-x: auto;
    display: flex;
    flex-direction: column;
    border-radius: 20px;
  }

  .close {
  margin: 10% 0 50% 16px;
  cursor: pointer;
  }

  .close-img {
  width: 25px;
  }

  .modal-header,
  .modal-footer {
    padding: 15px;
    display: flex;
  }

  /* .modal-header {
    font-family: cursive;
    position: relative;
    border-bottom: 1px solid #eeeeee;
    color: #ff9040;
    font-weight: bold;
    justify-content:left;
  } */

  .modal-header {
  font-weight: bold;
  font-size: 28px;
  color: #ff9040;
  text-align: left;
  margin-left: 60px;
  }

  .modal-footer {
    border-top: 1px solid #eeeeee;
    flex-direction: column;
    justify-content: flex-end;
  }

  .modal-body {
    position: relative;
    padding: 60px 200px;
  }

  /* .btn-close {
    position: absolute;
    top: 0;
    right: 0;
    border: none;
    font-size: 20px;
    padding: 10px;
    cursor: pointer;
    font-weight: bold;
    color: #ff9040;
    background: transparent;
  } */

  .btn-orange {
    color: white;
    background: #ff9040;
    border: 1px solid #ff9040;
    border-radius: 2px;
    width: 50%;
    padding-top: 10px;
    padding-right: 40px;
    padding-bottom: 10px;
    padding-left: 40px;
    text-align: center;
    margin: auto;
    border-radius: 8px;
  }

  .btn-orange:hover {
    color: white;
    background: darkorange;
    border: 1px solid darkorange;
    border-radius: 2px;
    width: 50%;
    padding-top: 10px;
    padding-right: 40px;
    padding-bottom: 10px;
    padding-left: 40px;
    text-align: center;
    margin: auto;
    border-radius: 8px;
  }

  .modal-fade-enter,
  .modal-fade-leave-to {
    opacity: 0;
  }

  .modal-fade-enter-active,
  .modal-fade-leave-active {
    transition: opacity .5s ease;
  }

  #image {
    float: left;
  }

  #name, #contact{
    float:left; 
    margin-right: 80px;
    margin-bottom: 50px;
    border-radius: 8px;
    width:230px; 
    height: 20px;
    padding: 2px;
  }
  #gender {
    float:left;
    border-radius: 8px;
    width:200px;
    height: 28px;
    padding: 2px;
  }
  
  #qualification{
    float:left;
    margin-right: 80px;
    margin-bottom: 50px;
    border-radius: 8px;
    width:230px; 
    height: 28px;
    padding: 2px;
  }

  #subjects {
    float:left;
    border-radius: 8px;
    margin-bottom: 60px;
    width:200px;
    height: 28px;
    padding: 2px;
  }

  #levels{
    float:left;
    margin-right: 80px;
    margin-bottom: 70px;
    border-radius: 8px;
    width:230px; 
    height: 28px;
    padding: 2px;
  }

  #location, #tele{
    float:left;
    margin-bottom: 50px;
    border-radius: 8px;
    width:230px; 
    height: 20px;
    padding: 2px;
  }
</style>