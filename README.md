# Optimal Control of Data Centers as Flexible Loads Under Uncertainty

<img width="512" height="512" alt="Data_Centers_Demand_Response" src="https://github.com/user-attachments/assets/c33cfba7-78bb-47a0-aa7c-d5ba0fd30d5e" />


This repository contains the implementation and simulation code for the research presented in the paper "[Optimal Control of Data Centers as Flexible Loads Under Uncertainty Conditions]([Link to your paper, e.g., arXiv or IEEE Xplore])" by Elinor Ginzburg-Ganz, Yoash Levron, and Anna Scaglione.

## 📄 Overview

The escalating demand for AI and machine learning applications is driving an unprecedented surge in data center energy consumption, posing significant challenges to existing electrical grid infrastructure. This project proposes a novel optimal control framework for the online management of data centers, transforming them into valuable grid assets through demand response mechanisms.

Traditional approaches often rely on computationally intensive, offline optimization models, hindering real-time implementation. Our methodology introduces an efficient algorithm that drastically reduces computational demands and control complexity, enabling real-time integration. This is achieved by leveraging an analytical solution for the optimal control law and employing a machine learning estimator to predict an integral term that encapsulates future uncertainties, rather than predicting full signal trajectories.

## ✨ Key Features

* **Optimal Control Framework:** Implementation of a novel optimal control strategy for data centers as flexible loads.
* **Uncertainty Handling:** Addresses pervasive uncertainties in incoming workload priorities and fluctuating power consumption.
* **Real-time Capability:** Designed for online operation with significantly reduced computational complexity.
* **Machine Learning Integration:** Utilizes an ML estimator to predict a crucial integral term ($\tilde{z}(t)$) for real-time control.
* **Computational Efficiency:** Demonstrates superior scalability and speedup compared to traditional Model Predictive Control (MPC) approaches.
* **Grid Stability & Economic Viability:** Shows how the framework enhances grid frequency regulation while considering data center operational profitability.
* **Fast Laplace Transform Acceleration:** Includes the implementation of the Fast Laplace Transform Approximation for accelerating training data generation.

## 🚀 Getting Started

These instructions will get you a copy of the project up and running on your local machine for development and testing purposes.

### Prerequisites

* Python 3.8+
* `pip` (Python package installer)

### Installation

1.  **Clone the repository:**
    ```bash
    git clone [https://github.com/your-username/data-center-optimal-control.git](https://github.com/your-username/data-center-optimal-control.git)
    cd data-center-optimal-control
    ```
2.  **Create a virtual environment (recommended):**
    ```bash
    python -m venv venv
    source venv/bin/activate  # On Windows: `venv\Scripts\activate`
    ```
3.  **Install dependencies:**
    ```bash
    pip install -r requirements.txt
    ```
    (You will need to create a `requirements.txt` file based on the Python code provided, e.g., `matplotlib`, `numpy`, `pandas`, `scikit-learn`, `tensorflow` or `pytorch` if used for the ML model.)

## 📊 Usage

The repository is structured to allow for simulation, training, and evaluation of the proposed framework.

1.  **Data Generation (Simulated):**
    The `data_generator.py` script (or equivalent) simulates data center workloads, power consumption, and grid signals. This also generates the $\tilde{z}(t)$ labels for ML training using the Fast Laplace Transform.
    ```bash
    python scripts/data_generator.py --duration 4weeks --output_file data/simulated_dataset.csv
    ```

2.  **Train the ML Estimator:**
    The `train_estimator.py` script trains the machine learning model to predict $\tilde{z}(t)$.
    ```bash
    python scripts/train_estimator.py --data_path data/simulated_dataset.csv --model_output models/zt_estimator.h5
    ```

3.  **Run the Optimal Control Simulation:**
    The `run_simulation.py` script executes the optimal control framework, comparing the proposed method against a baseline (e.g., MPC).
    ```bash
    python scripts/run_simulation.py --model_path models/zt_estimator.h5 --output_results results/simulation_output.csv
    ```

4.  **Generate Plots and Tables:**
    The `analyze_results.py` script generates the figures and tables presented in the paper.
    ```bash
    python scripts/analyze_results.py --results_path results/simulation_output.csv --output_dir figures_tables/
    ```

(Note: The script names and arguments are illustrative. You would adapt them to your actual code structure.)

## 📈 Results

The simulations demonstrate that the proposed optimal control framework significantly reduces computational time (up to 90x speedup for longer horizons) while effectively maintaining grid stability and meeting data center workload demands. The machine learning estimator for $\tilde{z}(t)$ achieves high accuracy (e.g., R$^2 > 0.90$). Economic analysis shows substantial annual savings and revenue generation for data center operators.

Refer to the `results/` directory for generated plots and tables that visually and quantitatively support these findings.

## 🤝 Contributing

Contributions are welcome! If you have suggestions for improvements, bug fixes, or new features, please open an issue or submit a pull request.

## 📝 License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details. (Create a `LICENSE` file in your repo if you don't have one).

## 📧 Contact

* Elinor Ginzburg-Ganz - [elinor.g12@gmail.com](mailto:elinor.g12@gmail.com)
* Yoash Levron - [yoashl@ee.technion.ac.il](mailto:yoashl@ee.technion.ac.il)
* Anna Scaglione - [as337@cornell.edu](mailto:as337@cornell.edu)

## 🙏 Acknowledgements

This work is based on the research presented in:
Ginzburg-Ganz, E., Levron, Y., & Scaglione, A. (2025). Optimal Control of Data Centers as Flexible Loads Under Uncertainty Conditions. *[Journal/Conference Name, if published]*.
