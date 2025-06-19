# FAKE_MEDIA_DETECTION

## Overview
This repository, `FAKE_MEDIA_DETECTION`, contains the implementation of a fake news detection system developed as a Bachelor of Technology project by K. Vaishnavi, Kunchala Kumar, and Ch. Ramakrishna at St. Peter's Engineering College, Hyderabad. The system integrates **Natural Language Processing (NLP)**, **Reinforcement Learning (RL)**, and **Blockchain** technology to detect and verify textual fake news, ensuring transparency and immutability of verification records. The project addresses the challenge of misinformation in digital media by combining linguistic analysis with decentralized storage.

## Features
- **NLP Preprocessing**: Tokenization, stop word removal, stemming, lemmatization, and vectorization using NLTK for text analysis.
- **Reinforcement Learning**: Adaptive classification of news as REAL or FAKE with a reward-penalty mechanism, outperforming traditional models like Random Forest.
- **Blockchain Verification**: Immutable storage of news metadata (hash, timestamp, authenticity score) on a local Ethereum blockchain using smart contracts.
- **IPFS Integration**: Decentralized storage of media files via InterPlanetary File System.
- **User Interface**: Web-based frontend for user registration, news submission, and viewing verification results.
- **Dataset**: Utilizes the BuzzFeed News dataset for training and evaluation.

## Installation
1. **Clone the Repository**:
   ```bash
   git clone https://github.com/GMohnish11/FAKE_MEDIA_DETECTION.git
   cd FAKE_MEDIA_DETECTION
   ```
2. **Install Dependencies**:
   ```bash
   pip install -r requirements.txt
   ```
   Ensure Python 3.7+ is installed. Key libraries include `nltk`, `sklearn`, `keras`, `web3.py`, `ipfsapi`, `django`, and `matplotlib`.
3. **Set Up Blockchain Environment**:
   - Install [Ganache](https://trufflesuite.com/ganache/) for a local Ethereum network.
   - Install [Truffle](https://trufflesuite.com/docs/truffle/getting-started/installation/): `npm install -g truffle`.
   - Deploy smart contracts:
     ```bash
     cd hello-eth
     truffle migrate
     ```
   - Start the blockchain server by running `runBlockchain.bat` in `hello-eth/node_modules/.bin/`.
4. **Set Up IPFS**:
   - Install [IPFS Desktop](https://ipfs.io/#install) or run an IPFS node.
   - Start the IPFS server by running `Start_IPFS.bat`.
5. **Start Python Server**:
   ```bash
   runServer.bat
   ```
6. **Access the Application**:
   Open a browser and navigate to `http://127.0.0.1:8000/index.html`.

## Usage
### User Workflow
1. **Sign Up/Login**:
   - Register via the "New User Signup Here" link.
   - Log in using credentials stored on the blockchain.
2. **Load Dataset**:
   - Click "Load BuzzFeed Dataset" to visualize real vs. fake news distribution.
3. **Train Model**:
   - Select "Train Reinforcement Learning" to train the RL model and compare with Random Forest (outputs RMSE, MAE, reward/penalty metrics).
4. **Publish News**:
   - Submit news text via "Publish News in Blockchain."
   - The system classifies it as REAL or FAKE, stores it on the blockchain, and returns a hash and transaction delay.
5. **View News**:
   - Access "View News" to see a table of published news, including publisher, text, hash, timestamp, and detection result.

### Example Commands
- **Train Model**:
  ```bash
  python src/train.py --dataset data/BuzzFeed_News.csv
  ```
- **Run Inference**:
  ```bash
  python src/inference.py --input "sample news text"
  ```

## Directory Structure
```
├── BlockchainFakeNews.json     # Smart contract ABI
├── data/                       # BuzzFeed News dataset (BuzzFeed_News.csv, Test_News.csv)
├── hello-eth/                  # Ethereum blockchain setup (Truffle, Ganache)
│   ├── node_modules/.bin/      # runBlockchain.bat
├── model/                      # RL model (model.json, model_weights.h5)
├── scripts/                    # Preprocessing and utility scripts
├── src/                        # Core source code
│   ├── inference.py            # Run detection on input text
│   ├── train.py                # Train RL model
│   ├── views.py                # Django backend logic
├── static/                     # Frontend assets (HTML, JS)
├── Start_IPFS.bat              # Start IPFS server
├── runServer.bat               # Start Django server
├── requirements.txt            # Python dependencies
├── session.txt                 # User session storage
└── README.md                   # Project documentation
```

## System Architecture
- **NLP Pipeline**: Processes text using NLTK for tokenization, stop word removal, stemming, lemmatization, and TF-IDF vectorization.
- **RL Model**: Classifies news as states, with actions (REAL/FAKE) rewarded or penalized based on accuracy.
- **Blockchain**: Uses Ethereum smart contracts (Solidity) for storing user and news data, with Web3.py for Python integration.
- **IPFS**: Stores media files decentrally, linked via hashes in blockchain records.
- **Frontend**: Django-based web interface with HTML/JavaScript for user interaction.

## Evaluation Results
- **Dataset**: BuzzFeed News dataset.
- **Metrics**:
  - Reinforcement Learning Model: Lower RMSE and MAE compared to Random Forest.
  - Adaptive learning via rewards/penalties enhances performance.
- **Performance Comparison**: Visualized in a graph (see `Screen 12` in documentation).

## Limitations
- **Scalability**: Blockchain transactions may introduce latency at scale.
- **Model Bias**: Dependent on dataset quality, may inherit biases.
- **Resource Intensive**: Requires significant computational power for NLP and blockchain operations.
- **Text-Only**: Currently limited to textual fake news detection.

## Contributing
We welcome contributions! To contribute:
1. Fork the repository.
2. Create a branch: `git checkout -b feature/your-feature`.
3. Commit changes: `git commit -m "Add your feature"`.
4. Push: `git push origin feature/your-feature`.
5. Submit a Pull Request.

Report issues via the [Issues](https://github.com/GMohnish11/FAKE_MEDIA_DETECTION/issues) tab.

## License
Licensed under the MIT License. See [LICENSE](LICENSE) for details.

## Acknowledgments
- **Guidance**: Dr. Amjan Shaik (Professor, Dean R&D) and Mr. A. Senthil Murugan (Project Coordinator).
- **Institution**: St. Peter's Engineering College, Hyderabad.
- **Dataset**: BuzzFeed News dataset.
- **References**: Research papers on fake news detection and blockchain (see project documentation).

## Contact
For inquiries, contact the project team via GitHub issues or reach out to St. Peter's Engineering College, Hyderabad.