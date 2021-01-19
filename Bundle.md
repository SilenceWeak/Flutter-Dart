# Bundle是主要用来跳转Activity时传输数据的，其中可以选择传送不同类型的数据如基本数据，可打包数据，可序列化数据  
* **Parcelable数据**
```
  public class Book implements Parcelable {  
      private String bookName;  
      private String author;  
      private int publishTime;  

      public String getBookName() {  
          return bookName;  
      }  
      public void setBookName(String bookName) {  
          this.bookName = bookName;  
      }  
      public String getAuthor() {  
          return author;  
      }  
      public void setAuthor(String author) {  
          this.author = author;  
      }  
      public int getPublishTime() {  
          return publishTime;  
      }  
      public void setPublishTime(int publishTime) {  
          this.publishTime = publishTime;  
      }  

      public static final Parcelable.Creator<Book> CREATOR = new Creator<Book>() {  
      @Override
          public Book createFromParcel(Parcel source) {  
              Book mBook = new Book();  
              mBook.bookName = source.readString();  
              mBook.author = source.readString();  
              mBook.publishTime = source.readInt();  
              return mBook;  
          }  
      @Override
          public Book[] newArray(int size) {  
              return new Book[size];  
          }  
      };  

    @Override
      public int describeContents() {  
          return 0;  
      }  

    @Override
      public void writeToParcel(Parcel parcel, int flags) {  
          parcel.writeString(bookName);  
          parcel.writeString(author);  
          parcel.writeInt(publishTime);  
      }  
  }  
```    
* **Serializable数据**
```
  public class Person implements Serializable {  

      private static final long serialVersionUID = 1L; 

      private String name;  
      private int age;  
      public String getName() {  
          return name;  
      }  
      public void setName(String name) {  
          this.name = name;  
      }  
      public int getAge() {  
          return age;  
      }  
      public void setAge(int age) {  
          this.age = age;  
      }  

  }  
```    
* **接收发送Parcelable数据**
```
  //发送数据
  private void sendParcelableDataThroughBundle(){  
      Intent intent = new Intent().setClassName("com.bundletest", "com.bundletest.Bundle02");

          Book mBook = new Book();
          mBook.setBookName("Android");
          mBook.setAuthor("skywang");
          mBook.setPublishTime(2013);

          Bundle mBundle = new Bundle();
          mBundle.putParcelable("ParcelableValue", mBook);
          intent.putExtras(mBundle);

          startActivity(intent);
      finish();
  }
 
 //接收Parcelable数据
  private void receiveParcelableData() {
    Book mBook = (Book)getIntent().getParcelableExtra("ParcelableValue");
    if (mBook != null)
      Log.d(TAG, "receice parcel data -- " +
             "Book name is: " + mBook.getBookName()+", "+
             "Author is: " + mBook.getAuthor() + ", "+
             "PublishTime is: " + mBook.getPublishTime());
  }
```    
* **接收发送Serializable数据**
```
  //发送数据
  private void sendSeriableDataThroughBundle(){  
    Intent intent = new Intent().setClassName("com.bundletest", "com.bundletest.Bundle02");

    Person mPerson = new Person();
        mPerson.setName("skywang");
        mPerson.setAge(24);

        Bundle mBundle = new Bundle();
        mBundle.putSerializable("SeriableValue",mPerson);
        intent.putExtras(mBundle);

        startActivity(intent);
    finish();
  }
 
    //接收Parcelable数据
  private void receiveSeriableData() {
    Person mPerson = (Person)getIntent().getSerializableExtra("SeriableValue");  
    if (mPerson != null){
      Log.d(TAG, "receice serial data -- " +
             "The name is:" + mPerson.getName() + ", "+
             "age is:" + mPerson.getAge());  
    }
  }
```    
* **接收发送基本类型数据**
```
  //发送数据
  private void sendBasicDataThroughBundle(){  
      // "com.test" is the package name of the destination class
      // "com.test.Activity02" is the full class path of the destination class
      Intent intent = new Intent().setClassName("com.bundletest", "com.bundletest.Bundle02");

      Bundle bundle = new Bundle();
      bundle.putString("name", "skywang");
      bundle.putInt("height", 175);
      intent.putExtras(bundle);

      startActivity(intent);

      // end current class
      finish();
  }
 
  //接收Parcelable数据
  private void receiveBasicData() {
    Bundle bundle = this.getIntent().getExtras();
    String name = bundle.getString("name");  
    int height = bundle.getInt("height");
    if (name != null && height != 0)
    Log.d(TAG, "receice basic data -- " +
           "name="+name+", height="+height);
  }
``` 
