const express = require('express');
const mongoose = require('mongoose');
const cors = require('cors');
const app = express();

// Middleware
app.use(cors());
app.use(express.json());

// The Connection String (with the %40 fix)
const dbURI = "mongodb+srv://admin:admin%40123@cluster0.zwkbjoe.mongodb.net/inventoryDB?retryWrites=true&w=majority";

mongoose.connect(dbURI)
    .then(() => console.log("✅ Database Connected!"))
    .catch(err => console.log("❌ Connection Error: ", err));

// Basic Route for testing
app.get('/', (req, res) => {
    res.send("Inventory API is running...");
});

// Port setup for hosting
const PORT = process.env.PORT || 5000;
app.listen(PORT, () => console.log(`Server live on port ${PORT}`));
