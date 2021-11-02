<template>
  <header>
    <div class="d-none d-md-block custom-header">
        <div class="row ">
          <nav class="navbar navbar-expand-lg navbar-light py-4 navbar-custom">
              <div class="container-fluid">
                <div class="col-md-3"><a class="navbar-brand" href="#"><img src="assests/logo.svg" alt=""></a></div>
                <div class="col-md-4" >
                    <form action="" class="search-form">
                      <i class="fas fa-search Search-icon"></i> <input type="text" name="" class="form-control Search" placeholder="Search....">
                    </form>
                </div>
                <div class="col-md-5 d-flex justify-content-around align-items-center">
                    <a href="" class="compeign-button text-center"><i class="fas fa-plus px-2"></i> New Compeign</a>
                    <a href="" class="notification"><i class="far fa-bell"></i><span>.</span></a>
                    <li class="nav-item dropdown text-secondary">
                      <a class="nav-link dropdown-toggle usermenu " href="#" id="navbarDarkDropdownMenuLink" role="button" data-bs-toggle="dropdown" aria-expanded="false">
                      <span class="text-dark username">Sandu Cosm </span>
                      <img src="assests/user.png" class="rounded" width="50" alt=""> 
                      </a>
                      <ul class="dropdown-menu dropdown-menu-dark" aria-labelledby="navbarDarkDropdownMenuLink">
                          <li><a class="dropdown-item" href="#">Action</a></li>
                          <li><a class="dropdown-item" href="#">Another action</a></li>
                          <li><a class="dropdown-item" href="#">Something else here</a></li>
                      </ul>
                    </li>
                </div>
              </div>
          </nav>
        </div>
    </div>
    <!-- header for mobile view -->
    <div class="row flex-row  mb-3 ">
        <div class="col-md-12 py-3 m-header d-flex justify-content-between flex-row d-md-none">
          <div>
              <button id="close" class="px-2 "><i class="fas fa-arrow-left"></i></button>
              <button id="open" class="px-2 "><i class="fas fa-bars"></i></button>
          </div>
          <h3>Create compaign</h3>
          <a href="" class="text-secondary userprofile-icon"><i class="fas fa-cog"></i></a>
        </div>
    </div>
    <!-- sidebar -->
    <div id="sidebar" class="d-block d-md-none">
        <div class="row">
          <div class="col-md-12 py-3 sidebar-logo">
              <img src="assests/logo.svg"  alt="">
          </div>
          <div class="col-md-12">
              <form action="" class="search-form">
                <i class="fas fa-search Search-icon"></i> <input type="text" name="" class="form-control Search bg-white" placeholder="Search....">
              </form>
          </div>
          <div class="col-md-12">
              <ul class="m-0 p-0 sidebar-list">
                <a href="">
                    <li><i class="fas fa-plus sidebar-icon"></i> new Compaign <span class="arrow">></span></li>
                </a>
                <a href="">
                    <li><img src="assests/users.svg" class="sidebar-icon" alt=""> Influence <span class="arrow">></span></li>
                </a>
                <a href="">
                    <li><img src="assests/compaign1.svg" class="sidebar-icon3" alt=""> Compaign <span class="arrow">></span></li>
                </a>
                <a href="">
                    <li><img src="assests/tags.svg" class="sidebar-icon4" alt=""> Deal <span class="arrow">></span></li>
                </a>
                <a href="">
                    <li><i class="fas fa-bell sidebar-icon"></i> notifications <span class="badge">4</span> <span class="arrow">></span></li>
                </a>
              </ul>
          </div>
        </div>
    </div>
  </header>
</template>

<style scoped>
</style>

<script>
export default {
  mounted() {
    //  javascript for sidebar  
    const open = document.getElementById('open');
    const close = document.getElementById('close');
    const sidebar = document.getElementById('sidebar');
    open.onclick = () => {
      sidebar.style.left=0;
      open.style.display = 'none';
      close.style.display = 'block';
    };
    close.onclick = () => {
      sidebar.style.left='-320px';
      close.style.display = 'none';
      open.style.display = 'block';
    };
  }
}
</script>