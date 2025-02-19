# 🌟 Laravel Eloquent Has-One-of-Many

Welcome to this guide on the **Has-One-of-Many** relationship in Laravel Eloquent! � This feature is incredibly useful when you want to retrieve a single record from a collection of related records. Let's dive in! �‍♂️

---

## 📌 What is Has-One-of-Many?

In Laravel Eloquent, the **Has-One-of-Many** relationship allows you to define a relationship where a model can have one specific record out of many related records. For example, if you have a `User` model and a `Post` model, you might want to retrieve the **latest post** or the **oldest post** for a user. This is where `Has-One-of-Many` comes into play! 🎯

---


## 🛠️ Installation
This feature is built into Laravel, so you don’t need to install anything extra! Just ensure you're using Laravel 8 or higher.

---

## 📌 Example Usage
### 🔹 Basic Example
Suppose you have a `User` model that has many `Orders`, but you only want to get the **latest order** for each user.

```php
class User extends Model
{
    public function latestOrder()
    {
        return $this->hasOne(Order::class)->latestOfMany();
    }
}
```

Now, you can access it like this:

```php
$user = User::find(1);
echo $user->latestOrder->id;
```

### 🔹 Oldest Record
If you need the **oldest order** instead, use:

```php
public function oldestOrder()
{
    return $this->hasOne(Order::class)->oldestOfMany();
}
```

### 🔹 Custom Column Selection
You can also retrieve the **highest-priced order** by specifying a custom column:

```php
public function highestPricedOrder()
{
    return $this->hasOne(Order::class)->ofMany('price', 'max');
}
```

Similarly, you can get the **lowest-priced order**:

```php
public function lowestPricedOrder()
{
    return $this->hasOne(Order::class)->ofMany('price', 'min');
}
```

---

## 🎯 When to Use Has-One-of-Many?
- Fetching the latest or oldest related record.
- Getting the most expensive or cheapest product/order.
- Selecting a specific related record based on a column value.

---

## 📜 Documentation
For more details, check out the **official Laravel documentation**: [Laravel Eloquent Relationships](https://laravel.com/docs/eloquent-relationships#one-of-many)

---

## 💡 Conclusion
Using **Has-One-of-Many** in Laravel makes querying related models more efficient and convenient. It helps in selecting only the most relevant record without fetching unnecessary data. 🚀✨

Happy coding! 🎉
