# Mortgage Calculator

This is a dynamic and interactive Mortgage Calculator application that calculates monthly mortgage payments based on user inputs. It uses JavaScript for calculations and Chart.js to visualize the payment breakdown.

## Features

- **Real-Time Calculations:** Updates calculations instantly as users modify input fields.
- **Interactive Chart:** Displays a doughnut chart of payment components: Principal & Interest, Property Tax, Home Insurance, and HOA fees.
- **Customizable Inputs:** Users can adjust:
  - Home price
  - Loan years
  - Down payment percentage
  - Interest rate
  - Property tax percentage
  - Home insurance amount
  - HOA fees

## Technologies Used

- **HTML5**: Structure of the web application.
- **CSS3**: Styling and layout.
- **JavaScript (ES6)**: Core logic for calculations and dynamic updates.
- **Chart.js**: Visualization of mortgage payment breakdown.

## Installation

1. Clone the repository:
   ```bash
   git clone https://github.com/your-username/mortgage-calculator.git
   ```
2. Navigate to the project directory:
   ```bash
   cd mortgage-calculator
   ```
3. Open `index.html` in your browser to run the application.

## Usage

1. Enter the home price, loan years, down payment, interest rate, property tax, home insurance, and HOA fees in the respective fields.
2. Adjust the slider inputs for finer control.
3. View the monthly payment breakdown in the doughnut chart and detailed summary below the form.

## Code Highlights

### JavaScript Core Logic

- **State Management:**
  ```javascript
  let state = {
    price: getNumber(document.querySelectorAll('[name="price"]')[0].value),
    loan_years: document.querySelectorAll('[name="loan_years"]')[0].value,
    down_payment: document.querySelectorAll('[name="down_payment"]')[0].value,
    interest_rate: document.querySelectorAll('[name="interest_rate"]')[0].value,
    property_tax: document.querySelectorAll('[name="property_tax"]')[0].value,
    home_insurance: document.querySelectorAll('[name="home_insurance"]')[0].value,
    hoa: document.querySelectorAll('[name="hoa"]')[0].value,
  };
  ```

- **Dynamic Chart Updates:**
  ```javascript
  function updateChart(chart, label, color) {
    chart.data.datasets.pop();
    chart.data.datasets.push({
      label: label,
      backgroundColor: color,
      data: [
        monthlyPrincipalInterest,
        monthlyPropertyTaxes,
        monthlyHomeInsurance,
        monthlyHOA,
      ],
    });
    chart.options.transitions.active.animation.duration = 0;
    chart.update();
  }
  ```

- **Monthly Payment Calculation:**
  ```javascript
  function calculateData() {
    totalLoan = state.price - state.price * (state.down_payment / 100);
    totalMonths = state.loan_years * 12;
    monthlyInterest = state.interest_rate / 100 / 12;
    monthlyPrincipalInterest =
      totalLoan *
      ((monthlyInterest * (1 + monthlyInterest) ** totalMonths) /
      ((1 + monthlyInterest) ** totalMonths - 1)).toFixed(2);
    ...
  }
  ```

## Screenshots

1. **Form Input and Chart Visualization:**
   ![Mortgage Calculator UI](screenshot-1.png)

2. **Monthly Payment Breakdown:**
   ![Payment Breakdown](screenshot-2.png)

## Future Enhancements

- Add support for multiple loan types (e.g., adjustable-rate mortgages).
- Implement user authentication for saving and retrieving calculations.
- Make the application mobile-friendly.

## Contributing

Contributions are welcome! Feel free to submit a pull request or open an issue to discuss any changes.

## License

This project is open-source and available under the [MIT License](LICENSE).

## Acknowledgments

- Reset CSS by [Eric Meyer](http://meyerweb.com/eric/tools/css/reset/)
- Chart.js library for visualizations.

---

