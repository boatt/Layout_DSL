# Layout_DSL
This library helps you to build Android layout with kotlin, getting rid of xml file, which has poor performance.

Inflating layout from xml file is time consuming. Because we have to load xml file to memory by I/O operation, then traverses tags in the xml files and create View instance by refelection.

This library creating layout by Kotlin, Thus we could get rid of this two process, just like the following:
```
class FirstFragment : Fragment() {
    private var ivBack:ImageView? = null
    private var tvTitle:TextView? = null

    private val rootView by lazy {
        ConstraintLayout {
            layout_width = match_parent
            layout_height = match_parent

            ivBack = ImageView {
                layout_id = "ivBack"
                layout_width = 40
                layout_height = 40
                margin_start = 20
                margin_top = 20
                src = R.drawable.ic_back_black
                start_toStartOf = parent_id
                top_toTopOf = parent_id
            }

            tvTitle = TextView {
                layout_width = wrap_content
                layout_height = wrap_content
                text = "commit"
                textSize = 30f
                textStyle = bold
                align_vertical_to = "ivBack"
                center_horizontal = true
            }
        }
    }

    override fun onCreateView(
        inflater: LayoutInflater, container: ViewGroup?,
        savedInstanceState: Bundle?
    ): View? {
        return rootView
    }

    private fun onBackClick() {
        activity?.finish()
    }

```
