<script>
  import "bubbles-ui/css/app.css";
  import { goto } from "$app/navigation";
  import { configStore } from "bubbles-ui";
  import { toastStore } from "bubbles-ui";
  import { 
      ToastContainer,
      SidebarPageWrapper, 
      Sidebar, 
      Modal
} from "bubbles-ui";
  $configStore.validate_on_blur = true;
  $configStore.toast_delay = 5500;
  $configStore.error_delay = 4500;
  $configStore.debug = true;
  $configStore.goto = goto;

  const sidebarConfig = {
    logo: "./logo.png", //you can import this and pass as a variable too
    sections: [
      {
        title: "Home",
        href: "/",
      },
      {
        title: "Settings",
        href: "/settings",
      },
    ],
  };
</script>
<!-- Toasts can occur between page transitions, because of forms, or other reasons.
It's easier to add them to the __layout.svelte file and add them to the DOM from
The store. More on that in the Toast section -->
<ToastContainer />

<!-- The sidebar can get added the layout. The SidebarPageWrapper will make sure your content
will look nice with the Sidebar. The rest of your content will be loaded in the <slot/> -->
<Sidebar {...sidebarConfig} />
<SidebarPageWrapper>
<slot />
</SidebarPageWrapper>

<!-- Modals usually are on top of everything. It's easy to add them here and then add content to
then and toggle them through included utility functions. More on this in the modal section -->
<Modal />