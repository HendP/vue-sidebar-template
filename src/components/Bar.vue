<template>
  <div id="wrapper">
    <aside id="sidebar-wrapper">
      <div class="sidebar-brand">
        <img src="../assets/img/vcs.png" alt="VOCS" width="180px" id="VOCS" />
      </div>
      <ul class="sidebar-nav">
        <li class="active">
          <a href="#"><i class="home icon"></i>Home</a>
        </li>
        <li>
          <a href="#"><i class="plug icon"></i>Plugins</a>
        </li>
        <li>
          <a href="#" v-b-toggle.collapse-1-inner @click="rotateArrow"
            ><i class="user icon"></i>Users<i
              class="angle right icon iconDropdown"
            ></i
          ></a>
          <b-collapse id="collapse-1-inner" class="mt-2">
            <ul style="list-style: none">
              <li class="active">
                <a href="#"><i class="home icon"></i>Home</a>
              </li>
              <li>
                <a href="#"><i class="plug icon"></i>Plugins</a>
              </li>
            </ul>
          </b-collapse>
        </li>
        <li>
          <a href="#"><i class="plug icon"></i>Plugins</a>
        </li>
        <li>
          <a href="#"><i class="plug icon"></i>Plugins</a>
        </li>
      </ul>
    </aside>

    <div id="navbar-wrapper" class="shadow-sm">
      <nav class="navbar navbar-inverse">
        <div class="container-fluid">
          <div class="navbar-header">
            <a
              href="#"
              class="navbar-brand"
              id="sidebar-toggle"
              @click="sidebarButton"
              ><i class="bars icon"></i
            ></a>
          </div>
        </div>
      </nav>
    </div>

    <section id="content-wrapper">
      <div class="row">
        <div class="col-lg-12">
          <h2 class="content-title">Test</h2>
          <p>
            Lorem, ipsum dolor sit amet consectetur adipisicing elit. Molestiae
            dolores doloremque quaerat suscipit quis culpa accusantium quidem
            libero omnis. Nobis laboriosam ipsum voluptatem qui distinctio ullam
            ipsam numquam tempora ab!
          </p>
        </div>
      </div>
    </section>
  </div>
</template>

<script>
export default {
  name: "Bar",
  data() {
    return {
      opened: false,
    };
  },
  methods: {
    sidebarButton: function (e) {
      let wrapper = document.querySelector("#wrapper");
      e.preventDefault();
      wrapper.classList.toggle("toggled");
    },
    rotateArrow: function (e) {
      let arrow = document.querySelector(".iconDropdown");
      e.preventDefault();

      if (arrow.style.transform === "") {
        arrow.style.transform = "rotate(90deg) translate(18px,-20px)";
        console.log("true");
      } else {
        arrow.style.transform = "";
        console.log("false");
      }
    },
  },
};
</script>

<style lang="scss">
body {
  padding-bottom: 30px;
  position: relative;
  min-height: 100%;
}

a {
  transition: background 0.2s, color 0.2s;
}
a:hover,
a:focus {
  text-decoration: none;
}

#wrapper {
  padding-left: 0;
  transition: all 0.5s ease;
  position: relative;
}

#sidebar-wrapper {
  z-index: 1000;
  position: fixed;
  left: 250px;
  width: 0;
  height: 100%;
  margin-left: -250px;
  overflow-y: auto;
  overflow-x: hidden;
  background: #003869;
  transition: all 0.5s ease;
}

#wrapper.toggled #sidebar-wrapper {
  width: 250px;
}

.sidebar-brand {
  background-color: #00539c;
  position: absolute;
  top: 0;
  width: 250px;
  height: 60px;
  text-align: center;
  padding: 20px 0;
}
.sidebar-brand h2 {
  margin: 0;
  font-weight: 600;
  font-size: 14px;
  color: #fff;
}

.sidebar-nav {
  position: absolute;
  top: 65px;
  width: 250px;
  margin: 0;
  padding: 0;
  list-style: none;

  li {
    text-align: left;
    line-height: 52px;

    a {
      display: block;
      text-decoration: none;
      color: #fff;
      font-weight: 600;
      font-size: 14px;
      i {
        font-size: 14px;
        width: 60px;
      }
    }

    a:hover,
    a:active {
      text-decoration: none;
      color: #003869;
      background: #fff;
    }
  }
}

#navbar-wrapper {
  width: 100%;
  position: relative;
  z-index: 2;
}

#navbar-wrapper .navbar {
  border-width: 0 0 0 0;
  background-color: #fff;
  font-size: 14px;
  height: 60px;
  margin-bottom: 0;
  border-radius: 0;
}
#navbar-wrapper .navbar a {
  color: #003869;
  font-size: 28px;
}
#navbar-wrapper .navbar a:hover {
  color: #f8be12;
}

#content-wrapper {
  width: 100%;
  position: absolute;
  padding: 15px;
  top: 0;
}

#sidebar-wrapper {
  width: 0;
}

#wrapper.toggled {
  padding-left: 250px;
}

#content-wrapper {
  position: relative;
  top: 0;
}

#wrapper.toggled #navbar-wrapper,
#wrapper.toggled #content-wrapper {
  position: relative;
  margin-right: 250px;
}

.iconDropdown {
  width: 24px;
  height: 24px;
  float: right;
  padding-top: 3px;
  // transform: rotate(90deg) translate(18px,-20px);
}
</style>