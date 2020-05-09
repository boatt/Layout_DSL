# Layout_DSL
This library helps you to build Android layout with kotlin, getting rid of xml file, which has poor performance.

Inflating layout from xml file is time consuming. Because we have to load xml file to memory by I/O operation, then traverses tags in the xml files and create View instance by refelection.

This two process is time consuming.

This library creating layout by Kotlin, Thus we could get rid of this two process, just like the following:
```
class FirstFragment : Fragment() {

    override fun onCreateView(inflater: LayoutInflater, container: ViewGroup?,savedInstanceState: Bundle?): View? {
        return buildViewByClDsl()
    }

    private fun buildViewByClDsl(): View =
        ConstraintLayout {
            layout_width = match_parent
            layout_height = match_parent

            ImageView {
                layout_id = "ivBack"
                layout_width = 40
                layout_height = 40
                margin_start = 20
                margin_top = 20
                src = R.drawable.ic_back_black
                start_toStartOf = parent_id
                top_toTopOf = parent_id
                onClick = { onBackClick() }
            }
       }
```
