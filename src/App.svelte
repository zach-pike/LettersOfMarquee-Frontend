<script lang="ts">
    import Navbar from "./Nav/Navbar.svelte";
    import NavbarItem from "./Nav/NavbarItem.svelte";
    import NavbarMainButtonGroup from "./Nav/NavbarMainButtonGroup.svelte";
    import NavbarSpacer from "./Nav/NavbarSpacer.svelte";
    import Home from "./Pages/Home.svelte";
    import Posts from "./Pages/Posts.svelte";

    import { Router, Link, Route } from "svelte-routing";

    let menuOpen = false;

    let url = "";
</script>

<Router {url}>
    <main class="h-screen w-screen flex flex-col">
        <Navbar>
            <NavbarItem showHoverBar={false}>
                <img class="h-full" src="buc.png" alt="Buc">
            </NavbarItem>

            <NavbarMainButtonGroup click={() => menuOpen = !menuOpen}>
                <NavbarItem showHoverBar={false}>
                    <p class="text-xl text-white font-bold hidden md:block">Letters of Marquee</p>
                </NavbarItem>
        
                <NavbarItem>
                    <Link to="/" class="text-white">Home</Link>
                </NavbarItem>
        
                <NavbarItem>
                    <Link to="/posts" class="text-white">Posts</Link>
                </NavbarItem>

                <NavbarItem>
                    <Link to="/about" class="text-white">About</Link>
                </NavbarItem>
                
                <NavbarSpacer />
        
                <NavbarItem>
                    <Link to="/login" class="text-white">Login</Link>
                </NavbarItem>
        
                <NavbarItem>
                    <Link to="/signup" class="text-white">Signup</Link>
                </NavbarItem>
            </NavbarMainButtonGroup>
        </Navbar>

        <!-- main content container -->
        <div class="w-screen h-full md:flex pt-12">

            <!-- Sliding side menu for phones -->
            <!-- Right -13rem is equivalent to the w-52 tag, it hides the menu off screen -->
            <div class="fixed bg-gray-300 w-52 p-4 duration-100 {menuOpen?"right-0":"right-[-13rem]"} drop-shadow-lg">
                <div class="w-full flex flex-col items-center">
                    <p class="text-xl">Menu</p>

                    <Link to="/" class="text-white">Home</Link>
                    <Link to="/posts" class="text-white">Posts</Link>
                    <Link to="/about" class="text-white">About</Link>
                    <Link to="/login" class="text-white">Login</Link>
                    <Link to="/signup" class="text-white">Signup</Link>
                </div>
            </div>

            <!-- Individual pages render here -->
            <Route path="/">
                <Home />
            </Route>

            <Route path="/posts">
                <Posts />
            </Route>
        </div>
    </main>
</Router>