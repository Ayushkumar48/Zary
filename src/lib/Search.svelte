<script>
  import {
    Navbar,
    NavBrand,
    NavLi,
    NavUl,
    Avatar,
    Dropdown,
    DropdownItem,
    DropdownHeader,
    DropdownDivider,
    Input,
  } from "flowbite-svelte";
  import { SearchOutline } from "flowbite-svelte-icons";
  import { onMount } from "svelte";

  let atTop = true;

  onMount(() => {
    const handleScroll = () => {
      atTop = window.scrollY === 0;
    };

    window.addEventListener("scroll", handleScroll);

    return () => {
      window.removeEventListener("scroll", handleScroll);
    };
  });
</script>

<div>
  <Navbar
    class={`flex items-center justify-between w-full ${atTop ? "inner2" : "inner"}`}
  >
    <NavBrand href="/">
      {#if atTop}
        <img
          src="../src/assets/Images/mylogo-icon.png"
          class="me-3 h-6 sm:h-9"
          alt="Flowbite Logo"
        />
        <span
          class="self-center whitespace-nowrap font-semibold dark:text-white navheading"
        >
          Zary
        </span>
      {:else}
        <img
          src="../src/assets/Images/mylogo-icon.png"
          class="me-3 h-6 sm:h-9 img img-scrolled"
          alt="Flowbite Logo"
        />
      {/if}
    </NavBrand>
    {#if atTop}
      <NavUl class="flex space-x-4 items-center">
        <NavLi><a href="/" class="navli-items">Home</a></NavLi>
        <NavLi><a href="/about" class="navli-items">Top Charts</a></NavLi>
        <NavLi><a href="/services" class="navli-items">Playlist</a></NavLi>
      </NavUl>
    {/if}
    <div class={"search-and-avatar"}>
      <div class={`${atTop ? "" : "navinput"}`}>
        <Input
          id="default-input"
          placeholder="search for your taste"
          class={`${atTop ? "input" : "input2"}`}
        >
          <SearchOutline
            slot="left"
            class="w-5 h-5 text-gray-500 dark:text-gray-400"
          />
        </Input>
      </div>
      <Avatar
        id="user-drop"
        class="cursor-pointer avatar"
        dot={{ color: "green" }}
      />
      <Dropdown triggeredBy="#user-drop">
        <DropdownHeader>
          <span class="block text-sm">Bonnie Green</span>
          <span class="block truncate text-sm font-medium"
            >name@example.com</span
          >
        </DropdownHeader>
        <DropdownItem>Dashboard</DropdownItem>
        <DropdownItem>Settings</DropdownItem>
        <DropdownItem>Earnings</DropdownItem>
        <DropdownDivider />
        <DropdownItem>Sign out</DropdownItem>
      </Dropdown>
    </div>
  </Navbar>
</div>

<style>
  .navheading {
    font-size: 1.8rem;
    font-weight: bold;
  }
  .img {
    background: azure;
    padding: 0.8vh;
    border-radius: 50vh;
    transition: all 0.6s ease;
  }
  .img-scrolled {
    transform: translateX(-2vw);
  }
  .search2 {
    display: flex;
    flex-direction: row;
    align-items: center;
    width: 100%;
  }
  :global(.input) {
    width: 20vw;
    height: 4.2vh;
    transition: width 0.6s ease;
  }
  :global(.input2) {
    width: 10vw;
    height: 4.2vh;
  }
  .navinput {
    transform: translateX(-35vw);
    transition: transform 0.5s ease;
  }
  :global(.inner2) {
    left: 0;
    top: 0;
    position: fixed;
    width: 100vw;
    height: 7vh;
    background: rgb(74, 74, 158) !important;
    color: aliceblue;
    transition:
      background 0.6s ease,
      height 0.6s ease;
  }
  :global(.inner) {
    left: 0;
    top: 0;
    position: fixed;
    width: 100vw;
    height: 7vh;
    background: transparent !important;
    color: aliceblue;
    transition:
      background 0.6s ease,
      height 0.6s ease;
  }
  .search-and-avatar {
    display: flex;
    flex-direction: row;
    gap: 3vh;
  }
  :global(.navli-items) {
    color: aliceblue;
    font-size: 1.05rem !important;
  }
  :global(.navli-items:hover) {
    color: red;
  }
  :global(.avatar) {
    width: 2.3vw;
    height: fit-content;
  }
</style>
