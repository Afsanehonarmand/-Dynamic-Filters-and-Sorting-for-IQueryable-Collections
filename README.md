# QueryableExtensions - Dynamic Filters and Sorting for IQueryable Collections

## Description

`QueryableExtensions` is a set of extension methods for the `IQueryable<T>` interface that provides dynamic filtering and sorting capabilities. This extension allows you to easily filter and sort data at runtime, without requiring hard-coded queries.

The key features include:
- **Dynamic Filtering**: Apply filters on any string property of the entity dynamically based on a keyword.
- **Dynamic Sorting**: Sort data based on a specified property and order (ascending or descending).

These extensions are particularly useful when building flexible and generic repositories, API endpoints, or services that need to handle dynamic queries.

## Features

- **Dynamic Filters**: Automatically filters the data based on a keyword provided, searching through all string properties of the entity.
- **Dynamic Sorting**: Sorts the data dynamically based on a given property name and direction (ascending or descending).
- **Flexible and Extensible**: Can be easily extended to support additional types of filtering or sorting, making it highly adaptable for various use cases.

## Installation

1. Clone or download this repository to your project directory.
2. Reference the `QueryableExtensions` file in your project.

## Usage

Once integrated, you can call these extension methods on any `IQueryable<T>` collection to apply dynamic filters and sorting.

### Example:

```csharp
using ArvanexBlazorApp.Domain.Extensions;
using System.Linq;

public class MyDataService
{
    private readonly IQueryable<MyData> _data;

    public MyDataService(IQueryable<MyData> data)
    {
        _data = data;
    }

    public IQueryable<MyData> GetFilteredData(string keyword, string? orderByProperty = null, bool isDescending = false)
    {
        var filteredData = _data.ApplyFilters(keyword); // Apply keyword-based filters
        var sortedData = filteredData.ApplySorting(orderByProperty, isDescending); // Apply dynamic sorting

        return sortedData;
    }
}
