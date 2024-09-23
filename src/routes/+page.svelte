<script>
  import { onMount } from "svelte";
  let selectedProduct = null;
  let showAlert = false;

  // Hide alert after 3 seconds
  const hideAlert = () => {
    setTimeout(() => showAlert = false, 3000);
  };

  onMount(async () => {
    const { Tooltip, Modal, Alert } = await import("bootstrap");

    // Initialize tooltips
    const tooltipTriggerList = document.querySelectorAll('[data-bs-toggle="tooltip"]');
    const tooltipList = [...tooltipTriggerList].map((el) => new Tooltip(el));

    // Function to initialize modals when "See more" is clicked
    const initModal = () => {
      const modalElement = document.getElementById('productModal');
      const modalInstance = new Modal(modalElement);

      // Open the modal when See more is clicked
      document.querySelectorAll('.btn-see-more').forEach((btn) => {
        btn.addEventListener('click', (event) => {
          const productId = event.target.dataset.productId;
          selectedProduct = products.find(p => p.id === parseInt(productId, 10));
          modalInstance.show();
        });
      });

      // Close the modal when the close button is clicked
      modalElement.addEventListener('hidden.bs.modal', () => {
        selectedProduct = null;
        showAlert = true;
        hideAlert();
      });
    };

    // Initialize the modals on load
    initModal();
  });

  const products = [
    { id: 1, name: "Product 1", description: "This is product 1", details: "Detailed info about Product 1" },
    { id: 2, name: "Product 2", description: "This is product 2", details: "Detailed info about Product 2" },
    { id: 3, name: "Product 3", description: "This is product 3", details: "Detailed info about Product 3" }
  ];
</script>

<!-- Alert for modal closure feedback -->
{#if showAlert}
  <div class="alert alert-success" role="alert">
    Modal closed successfully!
  </div>
{/if}

<!-- Product Cards with Accordion -->
<div class="row">
  {#each products as product}
    <div class="col-sm-4">
      <div class="card">
        <div class="card-body">
          <h5 class="card-title">{product.name}</h5>
          <p class="card-text" data-bs-toggle="tooltip" title="Product details">{product.description}</p>
          <button
            class="btn btn-primary btn-see-more"
            data-product-id={product.id}
            data-bs-toggle="tooltip"
            title="Click to see more details"
          >
            See more
          </button>
        </div>
      </div>
    </div>
  {/each}
</div>

<!-- Modal Template -->
<div
  class="modal fade"
  id="productModal"
  tabindex="-1"
  aria-labelledby="productModalLabel"
  aria-hidden="true"
>
  <div class="modal-dialog">
    <div class="modal-content">
      <div class="modal-header">
        <h5 class="modal-title" id="productModalLabel">{selectedProduct?.name}</h5>
        <button type="button" class="btn-close" data-bs-dismiss="modal" aria-label="Close"></button>
      </div>
      <div class="modal-body">
        {selectedProduct?.description}
      </div>
      <div class="modal-footer">
        <button
          type="button"
          class="btn btn-secondary"
          data-bs-dismiss="modal"
        >
          Close
        </button>
      </div>
    </div>
  </div>
</div>

<style>
  .card {
    margin-bottom: 20px;
  }
  .alert {
    margin-bottom: 20px;
  }
</style>
