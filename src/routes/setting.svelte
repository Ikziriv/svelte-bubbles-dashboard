<script>
    import { Header } from "bubbles-ui";
    
    const props = {
      title: "Page Title", //This will automatically set the page title for you unless you overwrite it with svelte:head
      breadcrumb_labels: ["Hello", "World"] //pass labels if you want to set your breadcrumbs manually. Generally only required if you have two dynamic IDs in your URLs next to each other
    }
    import { Row, RowBorder } from "bubbles-ui";
    import { Column100, Column50, Column } from "bubbles-ui";
    import { Center, Card } from "bubbles-ui";
</script>

<Header {...props} />
