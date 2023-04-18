# CO2 Calc App
This is a Blazor Server introduction project.

It shows the following points:
- Routing
- Components
- Bindings
- Events
- Methods

## Steps
### Create project and NavMenu
1. Create project Blazor Server App
2. Start project to check if it works
3. Add a Navlink into NavMenu.razor (copy and replace ***href, oi-icon and Name***)
```        
<div class="nav-item px-3">
    <NavLink class="nav-link" href="calc">
        <span class="oi oi-calculator" aria-hidden="true"></span> CO2 Output Calc
    </NavLink>
</div>
```
---
### Calc Page
1. Create Calc.razor Page in Pages
2. Add Page Routing `@page "/calc"`
3. Show result
4. Add PageTitle Component `<PageTitle>CO2 Output Calc</PageTitle>`
5. Change `<h3>` text to ***CO2 output***
6. Add label and input
```  
<label>Kilometres</label>
<input type="number" @bind="Kilometres"/>
```  
7. Create field Kilometres `private int Kilometres = 100;`
8. Create record Transportation 
```
public record Transportation(string? Title, double Co2PerKmInGramm);
```
9. Create List of Transportation and instance values
```
private List<Transportation> Transportations = new()
{
    new ("Car 🚗", 147),
    new ("Airplane 🛫", 230),
    new ("Train 🚝", 32)
};
```
10. Add foreach loop below input without variables
```
@foreach (var t in Transportations)
{
    <div class="card w-25 mt-2">
        <div class="card-body">
            <h2 class="card-title"></h2>
            <hr />
            <p class="card-text fw-bold"> kilograms</p>
        </div>
    </div>
}
```
11. Add Title to h5 `@t.Title`
12. Add Method to calculate
```
private double CalculateCo2InKg(double co2value) => (co2value * Kilometres) / 1000;
```
13. Add Method to card p class `@CalculateCo2InKg(t.Co2PerKmInGramm)`
14. Add `@bind:event="oninput"` to input.