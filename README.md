# Vaidhya-vega
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8" />
  <title>Smart Health & Nutrition Platform</title>

  <!-- Tailwind -->
  <script src="https://cdn.tailwindcss.com"></script>

  <!-- React -->
  <script src="https://unpkg.com/react@18/umd/react.development.js"></script>
  <script src="https://unpkg.com/react-dom@18/umd/react-dom.development.js"></script>

  <!-- Framer Motion -->
  <script src="https://unpkg.com/framer-motion/dist/framer-motion.umd.js"></script>

  <style>
    body {
      background: #0f172a;
    }
    .glow {
      box-shadow: 0 0 20px rgba(110,231,249,0.6);
    }
  </style>
</head>

<body>
  <div id="root"></div>

  <script type="text/javascript">
    const { useState } = React;
    const { motion } = window['framer-motion'];

    function App() {
      const [step, setStep] = useState(0);

      return (
        <div className="h-screen flex items-center justify-center text-white">
          {step === 0 && <Intro next={() => setStep(1)} />}
          {step === 1 && <Login next={() => setStep(2)} />}
          {step === 2 && <ModeSelection setStep={setStep} />}
          {step === 3 && <HealthMode next={() => setStep(4)} />}
          {step === 4 && <NutritionMode next={() => setStep(5)} />}
          {step === 5 && <FinalScreen />}
        </div>
      );
    }

    function Intro({ next }) {
      return (
        <motion.div
          className="text-center space-y-6 cursor-pointer"
          initial={{ opacity: 0 }}
          animate={{ opacity: 1 }}
          onClick={next}
        >
          <h1 className="text-4xl font-bold text-cyan-300">
            Smart Health & Nutrition Platform
          </h1>
          <p className="text-gray-300">
            Your Personal Wellness Assistant
          </p>

          <div className="flex justify-center gap-6 mt-6">
            <div className="w-10 h-10 bg-cyan-300 rounded-full glow"></div>
            <div className="w-10 h-10 bg-purple-400 rounded-full glow"></div>
          </div>

          <p className="text-sm text-gray-500">Click to continue</p>
        </motion.div>
      );
    }

    function Login({ next }) {
      const fields = ["Name", "Phone", "Address", "City", "State", "Email"];

      return (
        <motion.div
          className="bg-gray-900 p-8 rounded-xl glow space-y-4 w-80"
          initial={{ y: 50, opacity: 0 }}
          animate={{ y: 0, opacity: 1 }}
        >
          {fields.map((f) => (
            <input
              key={f}
              placeholder={f}
              className="w-full p-2 rounded bg-gray-800 outline-none"
            />
          ))}

          <button
            onClick={next}
            className="w-full bg-cyan-300 text-black py-2 rounded glow"
          >
            Get Started
          </button>
        </motion.div>
      );
    }

    function ModeSelection({ setStep }) {
      return (
        <div className="flex gap-10">
          <motion.button
            whileHover={{ scale: 1.1 }}
            onClick={() => setStep(3)}
            className="p-10 bg-cyan-300 text-black rounded-xl glow"
          >
            Health Mode
          </motion.button>

          <motion.button
            whileHover={{ scale: 1.1 }}
            onClick={() => setStep(4)}
            className="p-10 bg-purple-400 rounded-xl glow"
          >
            Nutrition Mode
          </motion.button>
        </div>
      );
    }

    function HealthMode({ next }) {
      const features = [
        "Video Consultation",
        "Patient Records",
        "Prescriptions",
        "Scanning Integration",
        "Doctor Interaction",
        "Appointments",
        "AI Prediction",
        "Pharmacy Delivery",
      ];

      return (
        <div className="grid grid-cols-2 gap-4">
          {features.map((f, i) => (
            <motion.div
              key={i}
              className="p-4 bg-gray-800 rounded glow"
              initial={{ opacity: 0 }}
              animate={{ opacity: 1 }}
              transition={{ delay: i * 0.2 }}
            >
              {f}
            </motion.div>
          ))}

          <button
            onClick={next}
            className="col-span-2 mt-4 bg-cyan-300 text-black py-2 rounded"
          >
            Next
          </button>
        </div>
      );
    }

    function NutritionMode({ next }) {
      return (
        <motion.div
          className="space-y-4 text-center"
          initial={{ opacity: 0 }}
          animate={{ opacity: 1 }}
        >
          <input
            placeholder="Enter Weight"
            className="p-2 bg-gray-800 rounded"
          />

          <input
            placeholder="Health Details"
            className="p-2 bg-gray-800 rounded"
          />

          <div className="p-4 bg-gray-800 rounded glow">
            Personalized Diet Plan Generated 🍎
          </div>

          <button
            onClick={next}
            className="bg-purple-400 px-4 py-2 rounded"
          >
            Continue
          </button>
        </motion.div>
      );
    }

    function FinalScreen() {
      return (
        <motion.div
          className="text-center space-y-6"
          initial={{ scale: 0.8, opacity: 0 }}
          animate={{ scale: 1, opacity: 1 }}
        >
          <div className="text-2xl text-cyan-300">
            Powered by Machine Learning
          </div>

          <h1 className="text-3xl font-bold">
            One Platform. Complete Health & Nutrition Care
          </h1>

          <p className="text-gray-400">
            Smart • Simple • Personalized
          </p>
        </motion.div>
      );
    }

    ReactDOM.createRoot(document.getElementById("root")).render(<App />);
  </script>
</body>
</html>
