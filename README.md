import openpyxl

def generate_template():
    # Create a new Excel workbook
    wb = openpyxl.Workbook()

    # Create a sheet for the data
    ws_data = wb.create_sheet("Data")

    # Add columns for the data
    ws_data.append(["Fecha", "Venta", "Proveedor", "Costo", "Caja"])

    # Create a sheet for the results
    ws_results = wb.create_sheet("Results")

    # Add columns for the results
    ws_results.append(["Total de ventas", "Total de proveedores", "Utilidad"])

    # Calculate the total sales
    ws_results["Total de ventas"].value = ws_data["Venta"].sum()

    # Calculate the total costs
    ws_results["Total de proveedores"].value = ws_data["Costo"].sum()

    # Calculate the profit
    ws_results["Utilidad"].value = ws_results["Total de ventas"].value - ws_results["Total de proveedores"].value

    # Save the workbook
    wb.save("template.xlsx")

if __name__ == "__main__":
    generate_template()

