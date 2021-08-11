<template>
  <div class="navbar netflix-font-sans-regular">
    <div class="navbar-container">
      <div class="menu-navigation">
        <a href="#" class="menu-logo">
          <img src="../assets/images/netflix-logo.png" />
        </a>
        <ul class="navigation-list">
          <li class="navigation-menu">
            <a href="#" class="text-bold">Home</a>
          </li>
          <li class="navigation-menu">
            <a href="#">TV Shows</a>
          </li>
          <li class="navigation-menu">
            <a href="#">Movies</a>
          </li>
          <li class="navigation-menu">
            <a href="#">New & Popular</a>
          </li>
          <li class="navigation-menu">
            <a href="#">My List</a>
          </li>
          <li class="navigation-menu">
            <a href="#">Watch Again</a>
          </li>
        </ul>
        <div class="nav-toolbar">
          <div class="nav-tool">
            <button>
              <font-awesome-icon :icon="['fas', 'search']" />
            </button>
          </div>
          <div class="nav-tool">
            <button>
              <font-awesome-icon :icon="['fas', 'bell']" />
            </button>
          </div>
          <div class="nav-tool">
            <div class="account">
              <div class="account-dropdown">
                <a href="#">
                  <span class="profile">
                    <div class="img-wrapper">
                      <img
                        src="../assets/images/profile.png"
                        alt=""
                        srcset=""
                      />
                    </div>
                  </span>
                </a>
                <span class="caret"></span>
              </div>
            </div>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>
