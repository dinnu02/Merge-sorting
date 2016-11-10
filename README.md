# Merge-sorting
void mergesort_divide(int [],int,int);
void mergesort_merge(int [],int,int,int);
void main()
{
 int a[20],n,i;
 clrscr();
 printf("\n Enter no.of elements to array");
 scanf("%d",&n);
 printf("\n Enter elements to array");
 for(i=0;i<n;i++)
 {
   scanf("%d",&a[i]);
 }
 printf("\n After sorting");
 mergesort_divide(a,0,n-1);
 for(i=0;i<n;i++)
 {
   printf("\t %d",a[i]);
 }
 getch();
}

void mergesort_divide(int a[],int first,int last)
{
  int mid;
  if(first<last)
  {
     mid=(first+last)/2;
     mergesort_divide(a,first,mid);
     mergesort_divide(a,mid+1,last);
     mergesort_merge(a,first,mid,last);
  }
}

void mergesort_merge(int a[],int first,int mid,int last)
{
  int temp[20],index,i,j;
  i=first;  /* i is starting position of the left sub array */
  j=mid+1;  /* j is starting position of the right sub array */
  index=first;   /* for temporary array */
  while(i<=mid  && j<=last)
  {
     if(a[i]<a[j])
     {
       temp[index]=a[i];
       i++;
       index++;
     }
     else
     {
       temp[index]=a[j];
       j++;
       index++;
     }
  }
  if(i>mid)
  {
    while(j<=last)
    {
      temp[index]=a[j];
      j++;
      index++;
    }
  }
  else
  {
    while(i<=mid)
    {
      temp[index]=a[i];
      i++;
      index++;
    }
  }
  for(i=0;i<index;i++)
  {
     a[i]=temp[i];
  }
}
