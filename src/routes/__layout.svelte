<script lang="ts">
  import "bubbles-ui/css/app.css";
  import { goto } from "$app/navigation";
  import { configStore } from "bubbles-ui";
  import { toastStore } from "bubbles-ui";
  
  import icon_arrow from "../assets/icons/arrow.svg";
  import { 
      ToastContainer,
      SidebarPageWrapper, 
      Sidebar, 
      IconButton, 
      showLoading, 
      hideLoading,
      Modal
} from "bubbles-ui";
  $configStore.validate_on_blur = true;
  $configStore.toast_delay = 5500;
  $configStore.error_delay = 4500;
  $configStore.debug = true;
  $configStore.goto = goto;

  const sidebarConfig = {
    logo: "./favicon.png", //you can import this and pass as a variable too
    sections: [
      {
        id: "dashboard",
        label: "Dashboard",
        title: "Dashboard",
        href: "/",
      },
      {
        id: "management",
        label: "Management",
        title: "Management",
        href: "/management",
      },
      {
        id: "report",
        label: "Report",
        title: "Report",
        href: "/report",
      },
      {
        id: "seting",
        label: "Setting",
        title: "Setting",
        href: "/setting",
      },
    ],
  };
  
  let y = 0;
</script>

<ToastContainer />
<svelte:window bind:scrollY={y} />
<Sidebar {...sidebarConfig} />

<SidebarPageWrapper>
<slot />
</SidebarPageWrapper>

<Modal />

{#if y > 1000}
  <div>
    <IconButton icon={icon_arrow} transparent={false} onclick={() => (y = 0)} />
  </div>
{/if}

<style>
  :global(p) {
    margin-bottom: 1rem;
    color: var(--gray-darker);
  }
  :global(.mt-2) {
    margin-top: 2rem;
  }
  div {
    position: fixed;
    bottom: 0;
    right: 0;
    margin-right: 20px;
    margin-bottom: 20px;
    z-index: 10;
  }
</style>