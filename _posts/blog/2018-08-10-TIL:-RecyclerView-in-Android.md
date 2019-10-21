---
layout: post
title:  "[TIL] Android RecyclerView"
date:   2018-12-2T16:52:00+07:00
author: anggoro_dwi
categories: Blog
tags: [TIL, Java, Android, Programing]
comments: true
share: true
mathjax: false
---

Pada Pengembangan android, ada modul yang bernama RecylerView. Singkatnya RecyclerView ini bertugas sebagai mengelola tampilan yang sifat data yang akan ditampilkan berupa List (bisa dikatakan Array Data). Contohnya seperti kalian buka aplikasi contact maka akan muncul nama-nama keluargamu, teman SD, teman tapi mesrah, dulu gebetan sekarang bukan, mantan .. dan ...ok STOP. Lalu apa kamu kira itu programer nulisin satu satu dicodingan(Hardcode) nya? terus waktu nulis mantanya baper gitu ?. hmm...

Wah? kenapa jadi ada postingan Android ini?
Ya, semoga ini menjadi langkah awal karir dijalan mobile. Menurutku sih,
seharusnya begitu ya, karir dibidang programing ini harus bisa lentur.
Tapi selentur-lenturnya pasti ada Constrain. Sebenernya ini saya belajar ini karena
dapet beasiswa dari program kominfo (Terimakasih kominfo). Kominfo membuat program 
yang namanya digitalent bekerja sama dengan dicoding (Terimakasih dicoding).
Disini sifatnya TIL ya, seperti ini catetan buat dirikusendiri jadi bakalan gak
detail detail banget dan btw ini categories nya Blog jadi nggak formal-formal 
banget. Kalo ada istilah yang bingung silahkan google lagi aja (Ngomong sama dirisendiri).
Kebanyakan copas dari [sini](https://developer.android.com/guide/topics/ui/layout/recyclerview)

# RecyclerView 

RecyclerView ini tugasnya adalah mengelola tampilan untuk menampilkan data 
yang banyak dengan format tampilan yang sama setiap datanya (entah bisa apa 
gak ya kalo dinamik, mungkin bisa). 
![Grafik sederhana dari RecyclerView](https://developer.android.com/training/material/images/RecyclerView.png)
Seperti grafik diatas ada bagian *LayoutManager* ,*Adapter*, dan *Dataset* yang perlu
disiapkan untuk diterapkan diandroid.

## Manfaatkan Palette

Masukkan RecyclerView dari Palette ke file *.xml didalam res/ folder, biarkan android
studionya yang bekerja buat nyiapin segalanya. (Aslinya gak tau, ini pasti sihir).

Atau kalau mau masukin manual buka file 'build.grader' untuk modul app.
Lalu tambahin berikut ([sumur](https://developer.android.com/guide/topics/ui/layout/recyclerview)) 

```
dependencies {
    implementation 'com.android.support:recyclerview-v7:28.0.0'
}
```
Setelah drag-drop RecyclerViewnya, maka akan tergenerasi code didalam *.xml nya
``` xml
<android.support.v7.widget.RecyclerView
    android:id="@+id/my_recycler_view"
    android:scrollbars="vertical"
    android:layout_width="match_parent"
    android:layout_height="match_parent"/>
```
yang perlu diperhatiin disitu untuk melangkah ke codingan logic nya adalah tag 
`android:id=@+id/my_recycler_view`.

## Inisialisasi 

Buat variable `RecyclerView`, `RecyclerView.Adapter` dan , `RecyclerView.LayoutManager`
``` java
public class MyActivity extends Activity {
    private RecyclerView recyclerView;
    private RecyclerView.Adapter mAdapter;
    private RecyclerView.LayoutManager layoutManager;

    @Override
    protected void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);
        setContentView(R.layout.my_activity);
        // nambil info dari file xml(yang sebenernya udah digenerasi ke objec R)
        // untuk RecyclerView berdasarkan id nya
        recyclerView = (RecyclerView) findViewById(R.id.my_recycler_view);

        // use this setting to improve performance if you know that changes
        // in content do not change the layout size of the RecyclerView
        recyclerView.setHasFixedSize(true);

        // use a linear layout manager
        // Bisa juga GridLayoutManager
        layoutManager = new LinearLayoutManager(this);
        recyclerView.setLayoutManager(layoutManager);

        // specify an adapter (see also next example)
        mAdapter = new MyAdapter(myDataset);
        recyclerView.setAdapter(mAdapter);
    }
    // ...
}
```

## Buat Adapternya

Seperti contoh ini

```java 
public class MyAdapter extends RecyclerView.Adapter<MyAdapter.MyViewHolder> {
    private String[] mDataset;

    // Provide a reference to the views for each data item
    // Complex data items may need more than one view per item, and
    // you provide access to all the views for a data item in a view holder
    public static class MyViewHolder extends RecyclerView.ViewHolder {
        // each data item is just a string in this case
        public TextView textView;
        public MyViewHolder(TextView v) {
            super(v);
            textView = v;
        }
    }

    // Provide a suitable constructor (depends on the kind of dataset)
    public MyAdapter(String[] myDataset) {
        mDataset = myDataset;
    }

    // Create new views (invoked by the layout manager)
    @Override
    public MyAdapter.MyViewHolder onCreateViewHolder(ViewGroup parent,
                                                   int viewType) {
        // create a new view
        TextView v = (TextView) LayoutInflater.from(parent.getContext())
                .inflate(R.layout.my_text_view, parent, false);
        ...
        MyViewHolder vh = new MyViewHolder(v);
        return vh;
    }

    // Replace the contents of a view (invoked by the layout manager)
    @Override
    public void onBindViewHolder(MyViewHolder holder, int position) {
        // - get element from your dataset at this position
        // - replace the contents of the view with that element
        holder.textView.setText(mDataset[position]);

    }

    // Return the size of your dataset (invoked by the layout manager)
    @Override
    public int getItemCount() {
        return mDataset.length;
    }
}

```

## Saya mengalami ...

Kesusahan ketika memahami flow dari adapternya. 








