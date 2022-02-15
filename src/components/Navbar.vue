<template>
    <nav id="navbar-example2" class="navbar">
        <a class="navbar-brand fw-bold fst-italic" href="/">AM</a>
        <button class="nav-toggle" aria-label="Abrir menú" @click="changeShow" >
            <i class="fas fa-bars"></i>
        </button>
        <ul class="navbar-ul">
            <li class="nav-item">
                <a class="nav-link" href="#main">Main</a>
            </li>
            <li class="nav-item">
                <a class="nav-link" href="#sobre-mi">Sobre Mi</a>
            </li>
            <li class="nav-item">
                <a class="nav-link" href="#mi-skills">Skills</a>
            </li>
            <li class="nav-item">
                <a class="nav-link" href="#mi-projects">Mis Proyectos</a>
            </li>
        </ul>
    </nav>
</template>

<script>

export default {
    setup() {
    },
};
</script>

<style lang="scss" scoped>
.navbar {
    position: fixed;
    top: 0;
    width: 100%;
    background-color: #6a7acf;
    padding-left: 10px;
    z-index: 2;
}

.navbar i {
    display: none;
}

.navbar a {
    color: #eaeafd;
    font-family: Oswald, cursive, Raleway, sans-serif;
    transition: color 0.4s;
}

ul {
    margin: 0;
    margin-block: 0;
    margin-inline: 0;
    padding: 0;
    padding-inline: 0;
}

.navbar a:hover {
    color: #202020;
    transition: color 0.4s;
}

.navbar-ul {
    display: flex;
    flex-direction: row;
    justify-content: space-evenly;
    list-style: none;
}
.nav-toggle {
    color: #fff;
    background: 0 0;
    border: none;
    font-size: 30px;
    padding: 0 20px;
    line-height: 60px;
    cursor: pointer;
    display: none;
}

@media (max-width: 425px) {
    .navbar i {
        display: block;
        color: #eaeafd;
        transition: color 0.4s;
        font-size: 20pt;
        margin-right: 10px;
    }
    .navbar i:hover {
        color: #202020;
        margin-right: 10px;
        transition: color 0.4s;
    }
    .navbar-ul {
        flex-direction: column;
        align-items: center;
        margin: 0;
        background-color: #39447a;
        position: fixed;
        top: 3.5rem;
        width: 100%;
        padding: 20px 0;
        height: calc(100% - 3.5rem);
        overflow-y: auto;
        left: 100%;
        transition: left 0.3s;
    }
    .navbar-ul a {
        font-size: 30pt;
    }
    .nav-toggle {
        display: block;
    }
    .nav-menu_visible {
        left: 0;
    }
    .nav-toggle:focus:not(:focus-visible) {
        outline: 0;
    }
    .section-mi__projects h2 {
        font-size: 40pt;
    }
}
@media (max-width: 270px) {
    .navbar-ul a {
        font-size: 20pt;
    }
    .section-mi__projects h2 {
        font-size: 30pt;
    }
}
</style>
