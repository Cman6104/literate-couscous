import yfinance as yf
import numpy as np
import google.generativeai as genai

genai.configure(api_key="Your API-KEY")




#Collect data on ticker
    
class Data:
    
    def __init__(self,ticker):
        self.ticker = yf.Ticker(ticker)
        self.balance_sheet = self.ticker.balance_sheet
        self.financials = self.ticker.financials
        self.cashflow = self.ticker.cashflow

    def get_data(self):
       
        return self.ticker,self.balance_sheet, self.financials, self.cashflow

#Calculate financial ratios using data from ticker

class Ratios:

    def __init__(self, data):
        self.ticker, self.balance_sheet, self.financials, self.cashflow = data 

    def get_data_for_ratios(self):
        
        current_assets = self.balance_sheet.loc["Current Assets"].iloc[0]
        current_liabilities = self.balance_sheet.loc["Current Liabilities"].iloc[0]
        total_assets = self.balance_sheet.loc["Total Assets"].iloc[0]
        total_liabilities = self.balance_sheet.loc["Total Liabilities Net Minority Interest"].iloc[0]
        shareholder_equity = self.balance_sheet.loc["Stockholders Equity"].iloc[0]
        inventory = self.balance_sheet.loc["Inventory"].iloc[0] if "Inventory" in self.balance_sheet.index else 0

        revenue = self.financials.loc["Total Revenue"].iloc[0]
        cost_of_goods_sold = self.financials.loc["Cost Of Revenue"].iloc[0]
        gross_profit = self.financials.loc["Gross Profit"].iloc[0]
        net_income = self.financials.loc["Net Income"].iloc[0]
        ebit = self.financials.loc["EBIT"].iloc[0]
        
        interest_expense = self.cashflow.loc["Interest Paid"].iloc[0] if "Interest Paid" in self.cashflow.index else 0
        number_of_shares = self.ticker.info['sharesOutstanding'] if 'sharesOutstanding' in self.ticker.info else np.nan 
        share_price = self.ticker.history(period="1d")['Close'].iloc[0]  

        return {
            "current_assets": current_assets,
            "current_liabilities": current_liabilities,
            "total_assets": total_assets,
            "total_liabilities": total_liabilities,
            "shareholder_equity": shareholder_equity,
            "inventory": inventory,
            "revenue": revenue,
            "cost_of_goods_sold": cost_of_goods_sold,
            "gross_profit": gross_profit,
            "net_income": net_income,
            "ebit": ebit,
            "interest_expense": interest_expense,
            "number_of_shares": number_of_shares,
            "share_price": share_price
        }
    def calculate_ratios(self):
       
        data = self.get_data_for_ratios()

        
        current_ratio = data["current_assets"] / data["current_liabilities"]
        quick_ratio = (data["current_assets"] - data["inventory"]) / data["current_liabilities"]
        debt_to_equity = data["total_liabilities"] / data["shareholder_equity"]
        return_on_assets = data["net_income"] / data["total_assets"]
        gross_profit_margin = data["gross_profit"] / data["revenue"]
        return_on_equity = data["net_income"] / data["shareholder_equity"]
        earnings_per_share = data["net_income"] / data["number_of_shares"]
        price_to_earnings = data["share_price"] / earnings_per_share

        
        return {
            "Current Ratio": current_ratio,
            "Quick Ratio": quick_ratio,
            "Debt to Equity": debt_to_equity,
            "Return on Assets (ROA)": return_on_assets,
            "Gross Profit Margin": gross_profit_margin,
            "Return on Equity (ROE)": return_on_equity,
            "Earnings Per Share (EPS)": earnings_per_share,
            "Price to Earnings (P/E)": price_to_earnings
        }

def get_ratios_for_ticker(ticker):
    data_object = Data(ticker)
    financial_data = data_object.get_data()
    ratios_object = Ratios(financial_data)
    return ratios_object.calculate_ratios()

#Main function to fetch calcualted ratios and ai response

if __name__ ==  '__main__':
    
    ticker = input("Hello, what is the ticker you want to analyze? ")

    ratios = get_ratios_for_ticker(ticker)

    ratios_text = "\n".join([f"{key}: {value:.2f}" for key, value in ratios.items()])
    
    model = genai.GenerativeModel("gemini-1.5-flash")

    prompt = f"""
    You are a financial analyst. Your job is to look at company financials and decide if the stock is a buy, hold, or sell.
    Here are the financial ratios for {ticker}:
    {ratios_text}
    Based on this information, what would your recommendation be for {ticker}?
    """

    response = model.generate_content(prompt)

    print(f"\nAI Recommendation for {ticker} based on financial ratios:")
    print(response.text)

 




