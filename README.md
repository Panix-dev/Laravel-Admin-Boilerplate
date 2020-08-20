# Laravel Admin Dashboard Boilerplate

> A boilerplate ready to use for your custom dashboard projects using Laravel

This repo contains the structure for an admin dashboard using the Laravel framework.


<br/>
<img src="https://camo.githubusercontent.com/0fc2018c171a0d6e721ad421391c006f316eee03/68747470733a2f2f63646e2e636f6c6f726c69622e636f6d2f77702f77702d636f6e74656e742f75706c6f6164732f73697465732f322f67656e74656c656c6c612d61646d696e2d74656d706c6174652d707265766965772e6a7067" title="Laravel" alt="Laravel">


## Table of Contents


> Try `clicking` on each of the `anchor links` below so you can get redirected to the appropriate section.


- [Gentelella Admin Theme](#gentelella-admin-theme)
- [Model Relationships](#model-relationships)
- [Storing Images](#storing-images)
- [Flash Messages](#flash-messages)
- [Admin Middleware](#admin-middleware)

- [Contact Details](#contact-details)


## Gentelella Admin Theme


Gentelella Admin is a free to use Bootstrap admin template. This template uses the default Bootstrap 4 styles along with a variety of powerful jQuery plugins and tools to create a powerful framework for creating admin panels or back-end dashboards. Theme uses several libraries for charts, calendar, form validation, wizard style interface, off-canvas navigation menu, text forms, date range, upload area, form autocomplete, range slider, progress bars, notifications and much more.

- :link: [Gentelella Admin Theme](https://github.com/ColorlibHQ/gentelella)


## Model Relationships


```php
public function movietags() {

	return $this->belongsToMany('App\Movietag', 'movie_movietag', 'movie_id', 'movietag_id');

}

public function moviecategory() {

	return $this->belongsTo('App\Moviecategory', 'category_id');

}

public function items() {

	return $this->belongsToMany('App\Item', 'item_movie', 'movie_id', 'item_id')->withPivot('item_id');

}
```


## Storing Images


```php
if ($request->hasFile('featured_image')) {
    $image = $request->file('featured_image');
    $filename = time().'.'.$image->getClientOriginalExtension();
    $location_preset = public_path('images_items/list_large/'.$filename);
    $location_preset_item = public_path('images_items/list_small/'.$filename);
    Image::make($image)->resize(702, null, function ($constraint) {
                            $constraint->aspectRatio();
                        })->crop(702,400)->save($location_preset);
    Image::make($image)->resize(445, null, function ($constraint) {
                            $constraint->aspectRatio();
                        })->crop(445,245)->save($location_preset_item);
}

$item->image = $filename;
```


## Flash Messages


```php
Notify::success('The modifications performed to the item have been updated successfully!', 'Item has been updated');
```


## Admin Middleware


```php
public function handle($request, Closure $next)
{
    if (Auth::user() &&  Auth::user()->user_type == 'admin') {
    	return $next($request);
    }
    return redirect('/');
}
```


## Contact Details


> :computer: [https://pagapiou.com](https://pagapiou.com)

> :email: [hello@pagapiou.com](mailto:hello@pagapiou.com)

> :iphone: [LinkedIn](https://www.linkedin.com/in/agapiou/)

> :iphone: [Instagram](https://www.instagram.com/panos_agapiou/)

> :iphone: [Facebook](https://www.facebook.com/panagiotis.agapiou)
