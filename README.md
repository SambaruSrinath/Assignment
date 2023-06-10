# Assignment
<!DOCTYPE html>
<html>
  <head>
    <style>
      .container {
        display: flex;
      }

      .box {
        flex: 1;
        padding: 20px;
        border: 1px solid black;
      }

      .item {
        display: flex;
        align-items: center;
        margin-bottom: 10px;
        cursor: move;
      }

      .item img {
        width: 80px;
        height: 40px;
        margin-right: 10px;
      }

      .item span {
        margin-left: 5px;
      }

      .drop-target {
        border: 2px dashed gray;
        padding: 20px;
        min-height: 100px;
      }

      .success-message {
        color: green;
        margin-top: 10px;
      }
      .reset-button-container {
        display: flex;
        justify-content: center;
        margin-top: 20px;
      }
    </style>
    <script>
      function handleDragStart(event) {
        event.dataTransfer.setData("text/plain", event.target.id);
      }

      function handleDragOver(event) {
        event.preventDefault();
        event.dataTransfer.dropEffect = "move";
      }

      function handleDrop(event) {
        event.preventDefault();
        const itemId = event.dataTransfer.getData("text/plain");
        const item = document.getElementById(itemId);
        event.target.appendChild(item);

        
        const existingMessage = event.target.querySelector(".success-message");
        if (existingMessage) {
          existingMessage.remove();
        }

       
        const successMessage = document.createElement("p");
        successMessage.textContent = "Item dropped successfully!";
        successMessage.classList.add("success-message");
        event.target.appendChild(successMessage);
      }
    </script>
  </head>
  <body>
    <div class="container">
      <div class="box">
        
        <h2>Container 1</h2>
        <div
          class="item"
          id="item1"
          draggable="true"
          ondragstart="handleDragStart(event)"
        >
          <img src="img1.jfif" alt="GrayDot Technology Pvt Ltd" />
          <span>GrayDot Technology Pvt Ltd</span>
        </div>
        <div
          class="item"
          id="item2"
          draggable="true"
          ondragstart="handleDragStart(event)"
        >
          <img src="img2.jfif" alt="GrayDOt Company" />
          <span>GrayDOt Company</span>
        </div>
        <div
          class="item"
          id="item3"
          draggable="true"
          ondragstart="handleDragStart(event)"
        >
          <img src="img3.jpg" alt="Security" />
          <span>Security</span>
        </div>
        <div
          class="item"
          id="item4"
          draggable="true"
          ondragstart="handleDragStart(event)"
        >
          <img src="img4.jfif" alt="Quote" />
          <span>Quote</span>
        </div>
      </div>
      <div
        class="box drop-target"
        ondragover="handleDragOver(event)"
        ondrop="handleDrop(event)"
      >
       
        <h2>Container 2</h2>
      </div>
    </div>
    <div class="reset-button-container">
      <button onclick="handleReset()">Reset</button>
    </div>
  </body>
</html>
