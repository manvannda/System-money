<!DOCTYPE html>
<html lang="km">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>ប្រព័ន្ធតាមដានចំណូលចំណាយប្រចាំថ្ងៃ</title>
    <!-- Tailwind CSS CDN -->
    <script src="https://cdn.tailwindcss.com"></script>
    <!-- Google Fonts: Battambang for Khmer script -->
    <link href="https://fonts.googleapis.com/css2?family=Battambang:wght@400;700&display=swap" rel="stylesheet">
    <style>
        /* Apply Battambang font to the body, with Inter as a fallback for Latin characters if needed */
        body {
            font-family: 'Battambang', 'Inter', sans-serif;
            background-color: #f0f2f5;
        }
        /* Custom scrollbar for better aesthetics */
        ::-webkit-scrollbar {
            width: 8px;
        }
        ::-webkit-scrollbar-track {
            background: #f1f1f1;
            border-radius: 10px;
        }
        ::-webkit-scrollbar-thumb {
            background: #888;
            border-radius: 10px;
        }
        ::-webkit-scrollbar-thumb:hover {
            background: #555;
        }
        @media print {
            body * {
                visibility: hidden;
            }
            #printable-area, #printable-area * {
                visibility: visible;
            }
            #printable-area {
                position: absolute;
                left: 0;
                top: 0;
                width: 100%;
            }
            .no-print {
                display: none !important;
            }
        }
    </style>
</head>
<body class="p-4 sm:p-6 md:p-8 lg:p-10 bg-gray-100 min-h-screen flex items-center justify-center">
    <div class="container mx-auto bg-white shadow-lg rounded-xl p-6 sm:p-8 md:p-10 w-full max-w-4xl border border-gray-200">
        <h1 class="text-3xl sm:text-4xl font-bold text-center text-gray-800 mb-8">ប្រព័ន្ធតាមដានចំណូលចំណាយប្រចាំថ្ងៃ</h1>

        <!-- Summary Section (Top) -->
        <div class="grid grid-cols-1 md:grid-cols-3 gap-4 mb-8 text-center" id="summary-section-top">
            <div class="bg-blue-100 p-4 rounded-lg shadow-sm border border-blue-200">
                <p class="text-lg text-blue-700">ចំណូលសរុប</p>
                <p class="text-2xl font-semibold text-blue-800" id="total-income-top">0.00 ៛</p>
            </div>
            <div class="bg-red-100 p-4 rounded-lg shadow-sm border border-red-200">
                <p class="text-lg text-red-700">ចំណាយសរុប</p>
                <p class="text-2xl font-semibold text-red-800" id="total-expense-top">0.00 ៛</p>
            </div>
            <div class="bg-green-100 p-4 rounded-lg shadow-sm border border-green-200">
                <p class="text-lg text-green-700">សមតុល្យ</p>
                <p class="text-2xl font-semibold text-green-800" id="balance-top">0.00 ៛</p>
            </div>
        </div>

        <!-- Add Transaction Section -->
        <div class="mb-8 p-6 bg-gray-50 rounded-lg shadow-md border border-gray-200">
            <h2 class="text-2xl font-semibold text-gray-700 mb-4">បញ្ចូលប្រតិបត្តិការថ្មី</h2>
            <div class="grid grid-cols-1 sm:grid-cols-2 lg:grid-cols-4 gap-4">
                <div>
                    <label for="transaction-description" class="block text-sm font-medium text-gray-700 mb-1">បរិយាយ</label>
                    <input type="text" id="transaction-description" placeholder="ទិញកាហ្វេ" class="mt-1 block w-full p-2 border border-gray-300 rounded-md shadow-sm focus:ring-blue-500 focus:border-blue-500">
                </div>
                <div>
                    <label for="transaction-amount" class="block text-sm font-medium text-gray-700 mb-1">ចំនួនទឹកប្រាក់</label>
                    <input type="number" id="transaction-amount" placeholder="10000" class="mt-1 block w-full p-2 border border-gray-300 rounded-md shadow-sm focus:ring-blue-500 focus:border-blue-500">
                </div>
                <div>
                    <label for="transaction-date" class="block text-sm font-medium text-gray-700 mb-1">កាលបរិច្ឆេទ</label>
                    <input type="date" id="transaction-date" class="mt-1 block w-full p-2 border border-gray-300 rounded-md shadow-sm focus:ring-blue-500 focus:border-blue-500">
                </div>
                <div>
                    <label class="block text-sm font-medium text-gray-700 mb-1">ប្រភេទ</label>
                    <div class="mt-1 flex space-x-4">
                        <label class="inline-flex items-center">
                            <input type="radio" name="transaction-type" value="income" class="form-radio text-green-600" checked>
                            <span class="ml-2 text-gray-700">ចំណូល</span>
                        </label>
                        <label class="inline-flex items-center">
                            <input type="radio" name="transaction-type" value="expense" class="form-radio text-red-600">
                            <span class="ml-2 text-gray-700">ចំណាយ</span>
                        </label>
                    </div>
                </div>
            </div>
            <button id="add-transaction-btn" class="mt-6 w-full bg-blue-600 text-white py-2 px-4 rounded-md hover:bg-blue-700 focus:outline-none focus:ring-2 focus:ring-blue-500 focus:ring-offset-2 shadow-md transition duration-150 ease-in-out">
                បន្ថែមប្រតិបត្តិការ
            </button>
        </div>

        <!-- Filter and Export Section - Removed as per user request -->
        <!--
        <div class="mb-8 p-6 bg-gray-50 rounded-lg shadow-md border border-gray-200 no-print">
            <h2 class="text-2xl font-semibold text-gray-700 mb-4">តម្រង និងនាំចេញ</h2>
            <div class="grid grid-cols-1 sm:grid-cols-2 gap-4 items-end">
                <div>
                    <label for="filter-month" class="block text-sm font-medium text-gray-700 mb-1">តម្រងតាមខែ</label>
                    <input type="month" id="filter-month" class="mt-1 block w-full p-2 border border-gray-300 rounded-md shadow-sm focus:ring-blue-500 focus:border-blue-500">
                </div>
                <div class="flex flex-col sm:flex-row gap-2">
                    <button id="export-csv-btn" class="w-full sm:w-1/2 bg-green-500 text-white py-2 px-4 rounded-md hover:bg-green-600 focus:outline-none focus:ring-2 focus:ring-green-500 focus:ring-offset-2 shadow-md transition duration-150 ease-in-out">
                        នាំចេញទៅ CSV
                    </button>
                    <button id="print-pdf-btn" class="w-full sm:w-1/2 bg-purple-500 text-white py-2 px-4 rounded-md hover:bg-purple-600 focus:outline-none focus:ring-2 focus:ring-purple-500 focus:ring-offset-2 shadow-md transition duration-150 ease-in-out">
                        បោះពុម្ព (PDF)
                    </button>
                </div>
            </div>
        </div>
        -->

        <!-- Transaction History Section -->
        <div class="p-6 bg-gray-50 rounded-lg shadow-md border border-gray-200" id="printable-area">
            <h2 class="text-2xl font-semibold text-gray-700 mb-4">ប្រវត្តិប្រតិបត្តិការ</h2>
            <div class="overflow-x-auto rounded-lg border border-gray-300 shadow-sm">
                <table class="min-w-full divide-y divide-gray-200">
                    <thead class="bg-gray-200">
                        <tr>
                            <th scope="col" class="px-4 py-3 text-left text-xs font-medium text-gray-600 uppercase tracking-wider">កាលបរិច្ឆេទ</th>
                            <th scope="col" class="px-4 py-3 text-left text-xs font-medium text-gray-600 uppercase tracking-wider">ម៉ោង</th>
                            <th scope="col" class="px-4 py-3 text-left text-xs font-medium text-gray-600 uppercase tracking-wider">បរិយាយ</th>
                            <th scope="col" class="px-4 py-3 text-left text-xs font-medium text-gray-600 uppercase tracking-wider">ចំនួនទឹកប្រាក់</th>
                            <th scope="col" class="px-4 py-3 text-left text-xs font-medium text-gray-600 uppercase tracking-wider">ប្រភេទ</th>
                            <th scope="col" class="px-4 py-3 text-left text-xs font-medium text-gray-600 uppercase tracking-wider no-print">សកម្មភាព</th>
                        </tr>
                    </thead>
                    <tbody class="bg-white divide-y divide-gray-200" id="transaction-list">
                        <!-- Transactions will be inserted here by JavaScript -->
                    </tbody>
                </table>
            </div>
            <p id="no-transactions-message" class="text-center text-gray-500 mt-4 hidden">មិនមានប្រតិបត្តិការណាមួយត្រូវបានរកឃើញទេ។</p>
        </div>
    </div>

    <script>
        // Array to store all transactions
        let transactions = [];

        // Get DOM elements
        const descriptionInput = document.getElementById('transaction-description');
        const amountInput = document.getElementById('transaction-amount');
        const dateInput = document.getElementById('transaction-date');
        const typeRadios = document.querySelectorAll('input[name="transaction-type"]');
        const addTransactionBtn = document.getElementById('add-transaction-btn');

        // Top Summary Elements
        const totalIncomeTopDisplay = document.getElementById('total-income-top');
        const totalExpenseTopDisplay = document.getElementById('total-expense-top');
        const balanceTopDisplay = document.getElementById('balance-top');

        const transactionList = document.getElementById('transaction-list');
        // Removed filterMonthInput, exportCsvBtn, printPdfBtn as their section is removed
        const noTransactionsMessage = document.getElementById('no-transactions-message');

        /**
         * Initializes the application by loading transactions from LocalStorage
         * and setting up event listeners.
         */
        function initializeApp() {
            loadTransactions();
            setDefaultDate();
            addEventListeners();
            renderTransactions(); // Initial render
            updateSummary(); // Initial summary update
        }

        /**
         * Sets the default date input to the current date.
         */
        function setDefaultDate() {
            const today = new Date();
            const year = today.getFullYear();
            const month = String(today.getMonth() + 1).padStart(2, '0'); // Months are 0-indexed
            const day = String(today.getDate()).padStart(2, '0');
            dateInput.value = `${year}-${month}-${day}`;
            // Removed setting default filter month as filter section is removed
        }

        /**
         * Adds all necessary event listeners to interactive elements.
         */
        function addEventListeners() {
            addTransactionBtn.addEventListener('click', addTransaction);
            // Removed event listeners for filter and export buttons
        }

        /**
         * Loads transactions from LocalStorage.
         */
        function loadTransactions() {
            const storedTransactions = localStorage.getItem('transactions');
            if (storedTransactions) {
                transactions = JSON.parse(storedTransactions);
            }
        }

        /**
         * Saves the current transactions array to LocalStorage.
         */
        function saveTransactions() {
            localStorage.setItem('transactions', JSON.stringify(transactions));
        }

        /**
         * Adds a new transaction based on user input.
         */
        function addTransaction() {
            const description = descriptionInput.value.trim();
            const amount = parseFloat(amountInput.value);
            const date = dateInput.value;
            const type = document.querySelector('input[name="transaction-type"]:checked').value;
            const now = new Date();
            const time = now.toLocaleTimeString('km-KH', { hour: '2-digit', minute: '2-digit' }); // Format time as HH:MM

            // Basic validation
            if (!description || isNaN(amount) || amount <= 0 || !date) {
                showMessage('សូមបញ្ចូលព័ត៌មានប្រតិបត្តិការឱ្យបានពេញលេញ និងត្រឹមត្រូវ។ (ចំនួនទឹកប្រាក់ត្រូវតែជាលេខវិជ្ជមាន)', 'red');
                return;
            }

            const newTransaction = {
                id: Date.now().toString(), // Unique ID for each transaction
                description,
                amount,
                date,
                time, // Store the time
                type
            };

            transactions.push(newTransaction);
            saveTransactions();
            clearForm();
            renderTransactions(); // Re-render to show new transaction
            updateSummary(); // Update summary
            showMessage('ប្រតិបត្តិការត្រូវបានបន្ថែមដោយជោគជ័យ!', 'green');
        }

        /**
         * Clears the transaction input form fields.
         */
        function clearForm() {
            descriptionInput.value = '';
            amountInput.value = '';
            setDefaultDate(); // Reset date to current date
            document.querySelector('input[name="transaction-type"][value="income"]').checked = true;
        }

        /**
         * Renders the transaction list based on the current filter.
         */
        function renderTransactions() {
            transactionList.innerHTML = ''; // Clear existing list
            // Removed filterMonth logic as filter section is removed

            // All transactions will be rendered, no filtering by month
            const transactionsToRender = transactions.slice().sort((a, b) => {
                // Sort by date, then by time (newest first)
                const dateA = new Date(`${a.date}T${a.time}`);
                const dateB = new Date(`${b.date}T${b.time}`);
                return dateB - dateA;
            });

            if (transactionsToRender.length === 0) {
                noTransactionsMessage.classList.remove('hidden');
            } else {
                noTransactionsMessage.classList.add('hidden');
                transactionsToRender.forEach(transaction => {
                    const row = document.createElement('tr');
                    row.className = 'hover:bg-gray-50';

                    const amountClass = transaction.type === 'income' ? 'text-green-600' : 'text-red-600';
                    const typeText = transaction.type === 'income' ? 'ចំណូល' : 'ចំណាយ';

                    row.innerHTML = `
                        <td class="px-4 py-3 whitespace-nowrap text-sm text-gray-800">${transaction.date}</td>
                        <td class="px-4 py-3 whitespace-nowrap text-sm text-gray-800">${transaction.time || ''}</td> <!-- Display time -->
                        <td class="px-4 py-3 whitespace-nowrap text-sm text-gray-800">${transaction.description}</td>
                        <td class="px-4 py-3 whitespace-nowrap text-sm font-medium ${amountClass}">${transaction.amount.toLocaleString('km-KH')} ៛</td>
                        <td class="px-4 py-3 whitespace-nowrap text-sm text-gray-800">${typeText}</td>
                        <td class="px-4 py-3 whitespace-nowrap text-right text-sm font-medium no-print">
                            <button data-id="${transaction.id}" class="delete-btn text-red-600 hover:text-red-900 ml-2">លុប</button>
                        </td>
                    `;
                    transactionList.appendChild(row);
                });
            }
            updateSummary(); // Update summary based on all transactions
            addDeleteEventListeners(); // Add listeners to new delete buttons
        }

        /**
         * Adds event listeners to all delete buttons.
         */
        function addDeleteEventListeners() {
            document.querySelectorAll('.delete-btn').forEach(button => {
                button.removeEventListener('click', deleteTransaction); // Prevent duplicate listeners
                button.addEventListener('click', deleteTransaction);
            });
        }

        /**
         * Deletes a transaction by its ID.
         * @param {Event} event - The click event from the delete button.
         */
        function deleteTransaction(event) {
            const transactionId = event.target.dataset.id;
            // Using a custom message box instead of confirm()
            showConfirmationModal('តើអ្នកពិតជាចង់លុបប្រតិបត្តិការនេះមែនទេ?', () => {
                transactions = transactions.filter(t => t.id !== transactionId);
                saveTransactions();
                renderTransactions();
                updateSummary();
                showMessage('ប្រតិបត្តិការត្រូវបានលុបដោយជោគជ័យ!', 'green');
            });
        }

        /**
         * Displays a confirmation modal instead of alert/confirm.
         * @param {string} message - The message to display in the modal.
         * @param {function} onConfirm - Callback function to execute if user confirms.
         */
        function showConfirmationModal(message, onConfirm) {
            const modalOverlay = document.createElement('div');
            modalOverlay.className = 'fixed inset-0 bg-gray-600 bg-opacity-50 flex items-center justify-center z-50';
            modalOverlay.innerHTML = `
                <div class="bg-white p-6 rounded-lg shadow-xl max-w-sm w-full text-center">
                    <p class="text-lg font-semibold mb-4 text-gray-800">${message}</p>
                    <div class="flex justify-center space-x-4">
                        <button id="confirm-yes" class="bg-red-500 text-white px-4 py-2 rounded-md hover:bg-red-600 transition duration-150 ease-in-out">បាទ/ចាស</button>
                        <button id="confirm-no" class="bg-gray-300 text-gray-800 px-4 py-2 rounded-md hover:bg-gray-400 transition duration-150 ease-in-out">ទេ</button>
                    </div>
                </div>
            `;
            document.body.appendChild(modalOverlay);

            document.getElementById('confirm-yes').addEventListener('click', () => {
                onConfirm();
                modalOverlay.remove();
            });

            document.getElementById('confirm-no').addEventListener('click', () => {
                modalOverlay.remove();
            });
        }

        /**
         * Updates the total income, total expense, and balance displayed for the top summary.
         * This function always displays totals for ALL transactions.
         */
        function updateSummary() {
            let totalIncomeAll = 0;
            let totalExpenseAll = 0;
            transactions.forEach(transaction => {
                if (transaction.type === 'income') {
                    totalIncomeAll += transaction.amount;
                } else {
                    totalExpenseAll += transaction.amount;
                }
            });
            const balanceAll = totalIncomeAll - totalExpenseAll;

            totalIncomeTopDisplay.textContent = `${totalIncomeAll.toLocaleString('km-KH')} ៛`;
            totalExpenseTopDisplay.textContent = `${totalExpenseAll.toLocaleString('km-KH')} ៛`;
            balanceTopDisplay.textContent = `${balanceAll.toLocaleString('km-KH')} ៛`;

            // Apply color based on balance for top summary
            if (balanceAll >= 0) {
                balanceTopDisplay.classList.remove('text-red-800');
                balanceTopDisplay.classList.add('text-green-800');
            } else {
                balanceTopDisplay.classList.remove('text-green-800');
                balanceTopDisplay.classList.add('text-red-800');
            }
        }

        // Removed exportToCSV function as the export section is removed

        /**
         * Displays a temporary message to the user.
         * @param {string} message - The message to display.
         * @param {string} type - The type of message (e.g., 'green' for success, 'red' for error, 'orange' for warning).
         */
        function showMessage(message, type) {
            const messageBox = document.createElement('div');
            messageBox.textContent = message;
            messageBox.className = `fixed bottom-4 right-4 p-3 rounded-lg shadow-lg text-white z-50 transition-opacity duration-300 ease-out`;

            if (type === 'green') {
                messageBox.classList.add('bg-green-500');
            } else if (type === 'red') {
                messageBox.classList.add('bg-red-500');
            } else if (type === 'orange') {
                messageBox.classList.add('bg-orange-500');
            } else {
                messageBox.classList.add('bg-gray-700');
            }

            document.body.appendChild(messageBox);

            // Fade out and remove after 3 seconds
            setTimeout(() => {
                messageBox.style.opacity = '0';
                setTimeout(() => {
                    messageBox.remove();
                }, 300);
            }, 3000);
        }

        // Initialize the app when the DOM is fully loaded
        document.addEventListener('DOMContentLoaded', initializeApp);
    </script>
</body>
</html>

