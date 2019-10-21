---
layout: post
title:  "[TIL] ViewModelProvider.Factory"
date:   2018-12-2T16:52:00+07:00
author: anggoro_dwi
categories: Blog
tags: [TIL, Java, Android, Programing]
comments: true
share: true
mathjax: false
---

Kali ini mau nyatet masalah metode '.Factory' di android. 

Sebenernya aku ngikutin tutorialnya [Android Kotlin Fundamentals 05.1](https://codelabs.developers.google.com/codelabs/kotlin-android-training-view-model/index.html?index=..%2F..android-kotlin-fundamentals#0) dikodelab. Nah aku menemukan hal yang lumayan sulit bagiku untuk memahaminya. btw, kenapa jadi konten blog nya banyak android ya. OK lain kali aku mau posting masalah kontrol sistem lah biar keliatan kaya sedang berusaha ngurusin thesis (inside awkward emoticon here). .... . Ok kita `return this.context()`.

# Factory

Ok, apakah itu ?.
Berdasarkan jawaban dari [Stackoverflow](https://stackoverflow.com/questions/7550612/in-simplest-terms-what-is-a-factory), jawaban teratas itu ngejelasin tenang kasus driver modul. Tapi yang perlu digaris bawah adalah 
> you do not need to have a single line of .... driver specific 'import' in your code. 

lalu jawaban kedua 
> Factory is an OO design pattern that deals with creating objects without specifying the exact class of object that is to be created. 

lalu jawaban terakhir yang menurut ku berhubungan kegunaan praktik nya
> Factory is an object for creating other objects.
> It creates objects without exposing the instantiation logic to the client.
> Use this pattern when you don't want to expose object instantiation logic to the client/caller

Nah aku pernah berfikiran, kenapa bikin instance obyek aja pakek faktory, padahal kan kalo bikin `new object` langsung aja di instance sekarang kan bisa.
Sebagai pengingat, kalo di MVVM android ini dibagian ViewModel dituntut untuk testable. Untuk mencapai ViewModel yang testable diharusnya untuk meminimalkan depedance.
Bisa dibaca [disini](http://rcardin.github.io/programming/software-design/java/scala/di/2016/08/01/resolve-problems-dependency-injection.html) buat contoh gimana depedencies itu, dan [disini](https://www.codeproject.com/articles/1131770/factory-patterns-simple-factory-pattern) buat contoh simple depedencies nya. Sebenarnya pingin rekonstruksi kasus khusus diandroid, tapi masih cupu, next aku update blognya deh. 

# Kenapa dan kapan harus pake ViewModelProvider.Factory ?

Berdasarkan atrikel [ini](https://medium.com/koderlabs/viewmodel-with-viewmodelprovider-factory-the-creator-of-viewmodel-8fabfec1aa4f)
> If your ViewModel have dependencies then you should pass this dependencies through the constructor (It is the best way to pass your dependencies), so you can mock that dependencies and test your ViewModel.

Diartikel itu juga ada kasus yang direkonstruksi kasus ViewModel dengan argumen. 
Setelah ini akan dibahas teknisnya

## Write ViewModel Android

Buat class `costumViewModel` yang punya argumen.
``` kotlin
class costumViewModel(voo: Int) : ViewModel() {
   var vaa = voo // ini perlu inisialisasi
   init {
       Log.i("costumViewModel", "final variable is $vaa")
   }
}
```
Bisa juga dengan cara ini ngelempar depedencies di argument nya.

## Write ViewModelFactory

```kotlin
class costumViewModelFactory(private var voo: Int) : ViewModelProvider.Factory {
    override fun <T : ViewModel?> create(modelClass: Class<T>): T {

        if (modelClass.isAssignableFrom(costumViewModel::class.java)) {
            return costumViewModel(voo) as T
        }
        throw  IllegalArgumentException("Unknown view model class")
    }
}
```

## Inisialisasi dicode Activity/Fragment

```kotlin
class costumFragment : Fragment() {
    private lateinit var viewModel: costumViewModel
    private lateinit var viewModelFactory: costumViewModelFactory

    override fun onCreateView(
            inflater: LayoutInflater,
            container: ViewGroup?,
            savedInstanceState: Bundle?
    ): View? {

        ....
        
        viewModelFactory = costumViewModelFactor(1412)
        viewModel = ViewModelProviders.of(this, viewModelfactory)
                       .get(costumViewModel::class.java) 
        viewModel.vaa //ini bisa diakses cuy.
        ....

    }
```

# Related Refrence

[1](https://alvinalexander.com/java/java-factory-pattern-example)
