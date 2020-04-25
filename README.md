# Android Basics

## Creating a custom row item
Step 1: Create a new resource file under layout call it as a list_row
Step 2: drag and drop a CardView on the file
Step 3: drag and drop a a linear view on the card view
Step 4: Add image view and text views
This will create your card view item

## Creating a Recycle view
Step 1 Drag and drop a Recycler view on ListActivity

## Creating adapters
Step 1 Create new packages like ui, model and data
Step 2 Create a Person class under model as follows

```
class Person {
    var name:String?=null
    var age:Int?=null
}
```

This represent a model class

Step 3: Create a Adapter class under data package called `PersonListAdapter`
Step 4: Accept a list of Person ArrayList<Person> and Context
Step 5: Extend the RecyclerView.Adapter<PersonListAdapter.ViewHolder>()
Step 6: Where ViewHolder is a inner class who accepts `View` and  implements `RecyclerView.ViewHolder(itemView)`
`onCreateViewHolder` will help to create the view from xml using `LayoutInflater`,
`onBindViewHolder` will bind the item at position to the view it give call to `ViewHolder` class
`ViewHolder` then assigns the values to the UI elements

## Binding the recycler view

Step 1: The activity where you dragged and dropped the `RecyclerView` add the following variables

```
    private var adapter: PersonListAdapter? = null
    private var personList: ArrayList<Person>? = null
    private var layoutManager: RecyclerView.LayoutManager? = null
```

Step 2: `onCreate` instantiate these variables like this

```
    personList = ArrayList()
    layoutManager = LinearLayoutManager(this)
    adapter = PersonListAdapter(this, personList!!)

    // setup list (Recycler View)
    recyclerView.layoutManager = layoutManager
    recyclerView.adapter = adapter
```

Step 3: Add items to the list
Step 4: Set the data set change event

```
    // notify adapter for data change
    adapter!!.notifyDataSetChanged()
```

## Adding a onClick listener for item in the list

Step 1: Implement `View.OnClickListener` for `PersonListAdapter` class
Step 2: Set the `setOnClickListener` for a given view in `ViewHolder` to the `PersonListAdapter` i.e. `this`

## Starting a new activity when clicked on list view item add the following code to onClick
```
    var name: TextView = itemView.findViewById(R.id.name) as TextView

    // start a new details activity
    var intent = Intent(ctx,DetailsActivity::class.java)
    intent.putExtra("name", name.toString())

    ctx.startActivity(intent)
```
